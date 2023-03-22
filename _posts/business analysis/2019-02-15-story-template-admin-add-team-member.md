---
date: 2019-02-15
title: Story template Admin add team member
category: business analysis
---
# Story template: Admin: add team member

```
h2. Business Value
*As an* Cons-admin/Pub-admin,
*I want to* add member to my team,
*So that* I can self-service grant my team members access to team's resources such as APIs.

h2. Common Knowledge
# *Role & Permission*: if not explicitly described otherwise, every functionality works the same for all user roles having permission using it. See [Role & Permission mapping|https://docs.google.com/spreadsheets/d/1cgtcZwBf59Yr7XZtCt_aLGcfM36Ek-BPc-6uJaLrMH0/edit#gid=0] for details.
# *Page Routing*: please follow [Page Routing Principles|https://docs.google.com/spreadsheets/d/1jYxtXSqwOxl3BY0v9iEs8GNMfu70hOXeDIqyvy-R-c8/edit#gid=501674950] if a page routing error occurs.
# *Security*: must follow [Security Guidelines|https://docs.google.com/spreadsheets/d/16rBYvFsEvN6ewTS3V4eQrCyeiifS1iw8HqDRobIXGgA/edit#gid=0].

h2. Acceptance Criteria
+AC1 Admin can see add button is disabled by default+
*GIVEN* Emma in User Center page,
*THEN* she can see the Add button in team member list is disabled.

+AC2 Admin can only see users logged in ThoughtAPI in autocomplete dropdown+
*GIVEN* Emma in User Center page,
*WHEN* she clicks Add Team Member input area (see UI Spec),
*AND* she directly types in a user name or email,
*THEN* as she types in every single character of a user name or email, she can immediately see a autocomplete dropdown (see UI Spec) with users (logged in ThoughtAPI before) matching typed words.

+AC3 Admin can not see user already existed in her own team to her own team+
*GIVEN* Emma in User Center page,
*WHEN* she clicks Add Team Member input area (see UI Spec),
*AND* she directly types in a user name or email,
*THEN* as she types, she can see a autocomplete dropdown (see UI Spec) with users (within ThoughtAPI but outside his team) matching typed words,
*AND* she can NOT see users already in his team in autocomplete dropdown.

+AC4 Admin can select a user from autocomplete dropdown+
*GIVEN* Emma sees a autocomplete dropdown (see UI Spec) with users matching typed words,
*WHEN* she selects a user in autocomplete dropdown,
*THEN* the user's NAME_AND_EMAIL (see UI Spec) will appear in input area,
*AND* the Add buton is enabled.

+AC5 Admin can add user to her own team+
*GIVEN* Emma selected a user in autocomplete dropdown,
*WHEN* she clicks Add Button (see UI Spec),
*THEN* the add button is immediately disabled,
*AND* if operation is successful, she can see a SUCCESS_BANNER_MESSAGE (see UI Spec) in header,
* user is added as a publisher,
* the user immediately appears in the member list in order (see Sort Rules for Team member list),
* text in input area is cleared,

*AND* if operation is failed due to 5XX error, she can see a 5XX_FAILURE_BANNER_MESSAGE (see UI Spec) in header,
* the add buton is enabled,
* text in input area is NOT cleared,

*AND* if operation is failed due to 404 error, she can see a 404_USER_NOT_FOUND_ERROR_MESSAGE (see UI Spec) next to input,
* the add buton is enabled,
* text in input area is NOT cleared,

*AND* if operation is failed due to 409 error, she can see a 409_USER_CONFLICT_ERROR_MESSAGE (see UI Spec) next to input,
* the add buton is enabled,
* text in input area is NOT cleared,

+AC6 Admin can see add button is disabled if she changes input text+
*GIVEN* Emma selected a user in autocomplete dropdown,
*AND* Add button is enabled,
*WHEN* she clicks Add Team Member input area (see UI Spec),
*AND* she changes text,
*THEN* Add buton is disabled.

+AC7 Admin can see error message disappear if she changes input text+
*GIVEN* Emma sees a 404_USER_NOT_FOUND_ERROR_MESSAGE or 409_USER_CONFLICT_ERROR_MESSAGE (see UI Spec) next to input,
*WHEN* she clicks Add Team Member input area (see UI Spec),
*AND* she changes text,
*THEN* the error message disappears.

+AC8 Admin can see a no record match message if user typed not found+
*GIVEN* Emma in User Center page,
*WHEN* she clicks Add Team Member input area (see UI Spec),
*AND* she directly types in a user name or email,
*THEN* if the name she typed is not found in ThoughtAPI, she can see the autocomplete dropdown with only one row with NO_RECORD_FOUND_ERROR_MESSAGE (see UI Spec).

+AC9 Admin can see 5xx error banner message only once during her typing if 5XX error occurs+
*GIVEN* Emma in User Center page,
*WHEN* she types in a team member name or email,
*AND* during his typing, 5XX error occurs,
*THEN* she can only see 5XX_FAILURE_BANNER_MESSAGE for ONCE during his typing,
*AND* if she stops typing and starts typing again with a time interval less than 1 second, she will NOT see another 5XX_FAILURE_BANNER_MESSAGE,
*AND* if she stops typing and starts typing again with a time interval long than 1 second, she will see another 5XX_FAILURE_BANNER_MESSAGE.

h2. UI Spec
link: https://preview.uxpin.com/c8d4194e8f4122661829775772b1a94109300243#/pages/96627897/simulate/no-panels?mode=i

*Screenshots*

*Add Team Member*
placeholder: 
{noformat}
Add team member here...
{noformat}

*Add Button*
text:
{noformat}
Add
{noformat}

NAME_AND_EMAIL:
{noformat}
Shunfa Xu (sfxu@thoughtworks.com)
{noformat}

*Sort Rules for Team member list*
Sort By: Last Name
Case Sensitive: No
Order: [a-z 其他字符(按ASCII排序)]

see examples in TMA-386

*Autocomplete Dropdown (users)*
1. dropdown item text format: 
{noformat}
Shunfa Xu (sfxu@thoughtworks.com)
{noformat}

2. Match Rules
* Precisely match initials of username and email
* Case insenstive

Example:
Searching for Shunfa Xu (sfxu@thoughtworks.com),
will match with following keywords：

{noformat}
Shun, Sh X, S Xu, Shunfa, Shunfa Xu, sf, sfxu, sfxu@thought, sfxu@thoughtworks.com,  Shunfa Xu sfxu@thoughtworks.com
{noformat}


will NOT match with following keywords：

{noformat}
Sun, S Xa, Shunfaxu, Shunfa L, sxu, sxu@thoughtworks.com,  ShunfaXu sfxu@thoughtworks.com
{noformat}

4. Max length of dropdown: 6个item的高度，所有匹配结果全部加载，dropdown可以上下滚动
5. Pagination support: NO 
4. Sort by: none

*Text*
PLACEHOLDER 
{noformat}
type here...
{noformat}

SUCCESS_BANNER_MESSAGE
{noformat}
Save successful
{noformat}

5XX_FAILURE_BANNER_MESSAGE
{noformat}
Something is wrong, please try again later
{noformat}

404_USER_NOT_FOUND_ERROR_MESSAGE
{noformat}
User is not found
{noformat}

409_USER_CONFLICT_ERROR_MESSAGE
{noformat}
User is already in the team
{noformat}

NO_RECORD_FOUND_ERROR_MESSAGE
{noformat}
There is no record that match your search
{noformat}

*Test Seriro*
# Admin can see add button/area in user center - member area.
# Publisher can't see add button/area in user center - team member area & editText.
# Admin can input member name or email in editText. It will show a list which include input,(top 10)
# member list name should not same with publisher's team.
# Admin only can select user in list, it input info which not include, it will not save. 
# Admin click add button, it will add new member. When page get response, add button is not clickable. And after add successful.
# Open two same center page, choice one create a member and save it. Then input same member in another page, it will show error message which means it have been exciting.
```
