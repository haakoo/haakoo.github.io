---
layout: post
cover: 'assets/images2/2017/07/Gitlab-nested-AD-groups-Unsplash-tyler-lastovich-272588-edited.jpg'
navigation: True
title: Using nested AD groups to filter access to Gitlab
date: '2017-07-15 18:30:00'
tags:
- english
- gitlab
- active-directory
subclass: 'post' #important(!)
author: haakoo
categories: haakoo
---

I struggled while trying to limit access to our internal omnibus Gitlab instance using the LDAP-setting `user_filter:`. We use nested groups in Microsoft AD to handle users and access rights, which works with Gitlab, when you know about the secret sauce.

## Licensing - you need an enterprise license
First I tried getting it to work with our Gitlab instance which is running the free community edition. I read through the docs about [LDAP](https://docs.gitlab.com/ce/administration/auth/ldap.html), added `user_filter:` to our settings file and it didn't work. Users that were added directly to the AD group that was used as a filter got access, but not users in groups in the "main" group, e.g. the group *Gitlab-access* contains *User1* and *User2* and *Engineering-group*, and *Enginerring-group* contains *User3*. Using the following filter:

```ruby
user_filter: '(&(objectClass=person)(memberOf=cn=Gitlab-access,dc=domain,dc=com)'
```

will only grant access to *User1* and *User2*, not *User3*.

This was't a trivial discovery, since the Gitlab [CE documentation](https://docs.gitlab.com/ce/administration/auth/ldap.html#using-an-ldap-filter-to-limit-access-to-your-gitlab-server) seems to indicate that nested AD groups work. It's only once you see that the [LDAP Additions to Gitlab EE documentation](https://docs.gitlab.com/ee/administration/auth/ldap-ee.html#supported-ldap-group-types-attributes) also mention nested AD groups that you realise this might be an EE feature.

I went along and asked for an EE trial license to see if I could get it to work.

*__Edit 2017-07-18:__ It turns out that it is possible to use nested AD groups with `user_filter:` in Gitlab CE. After I contacted Gitlab about the confusion the documentation has been [updated](https://gitlab.com/gitlab-org/gitlab-ce/merge_requests/12871).*

## Special AD LDAP query rules
The second hurdle was to realise that the *plain* LDAP query I show higher up wont work because of Microsoft AD. You need to add a special rule object identifier (OID) to get a *recursive* version of `memberOf` called `LDAP_MATCHING_RULE_IN_CHAIN`. More information over at [MDSN](https://msdn.microsoft.com/en-us/library/aa746475(v=vs.85).aspx):

> This rule is limited to filters that apply to the DN. This is a special "extended" match operator that walks the chain of ancestry in objects all the way to the root until it finds a match.

The resources that helped me understand this were mainly the Stackoverflow questions [ldap nested group membership](https://stackoverflow.com/questions/6195812/ldap-nested-group-membership) and [Can LDAP\_MATCHING\_RULE\_IN\_CHAIN return 'subtree search results' with attributes (specifically “memberOf”)?](https://stackoverflow.com/questions/9945518/can-ldap-matching-rule-in-chain-return-subtree-search-results-with-attributes). I also found some information over at Atlassians help page [Active Directory user filter does not search nested groups](https://confluence.atlassian.com/crowdkb/active-directory-user-filter-does-not-search-nested-groups-715130424.html)

The `user_filter:` setting that finally worked was the following:

```ruby
user_filter: '(&(objectClass=person)(memberOf:1.2.840.113556.1.4.1941:=cn=Gitlab-access,dc=domain,dc=com)'
```

--- 

Cover photo [Simple Circles](https://unsplash.com/photos/9Eheu3sIgrM) by [Tyler Lastovich](https://unsplash.com/@lastly) from [Unsplash](https://unsplash.com/)
