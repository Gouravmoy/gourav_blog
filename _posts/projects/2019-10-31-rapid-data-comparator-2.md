---
title:  "Rapid Data Comparator2"
author: "Steve"
permalink: /blog/project/rdc2.html
---
[[_TOC_]]
## General Analysis

1. We will have 3 types of comments
    - Public comment
    - Pure Private comment (comments with named recipients)
    - Restricted comment (comments with access tags) (Work-Note for My Tech)
2. We will allocate `2` as the comment type for Restricted comments
 
## My Tech Analysis

1. OneForm will store the access tags for the process. This will be set in the process settings page
2. UI will get the access tags from the integrating application.
3. UI will provide the access tags to discussion service
4. One Form will also provide the settings for UI configuration for comments. So weather Work Notes are enabled or disabled/ pure private comments are enabled or disabled are stored at the process settings level at One Form side
5. These settings are passed on to the UI which will accordingly show the view

## UI Configuration
1. The UI component will be provided with a configuration attribute
2. The configuration attribute will define the **input view**
3. Below are the possible values for the attribute
    - `default` - Public Comment View
    - `restricted` - Public + Restricted Comment View
    - `private` - Public + Private Comment View
    - `all` - Public + Private + Restricted Comment View 

## API Required
### New API's
1. Get all access tags

### Existing API's
1. Get all members by request Id API should also support getting members by request Id and access tags
2. Check Access API should also support checking access by access tags
## Questions

1. Is there a possibility where there will be overlap in comment types. For example, A restricted comment can also have recipients tagged to it along with access tags
2. What about Notification part. At present private comments have a list of notification recipients same as their audience. What should be done in case of access tags and public comments
3. Access tags are supposed to be dynamic. When a new step member is added or removed, they should be able to see/not see the comment. But OneForm does not add/remove the new members. Its a known functionality. How will the dynamic access tags work then.
