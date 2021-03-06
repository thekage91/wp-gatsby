# Change Log

## 0.6.0

- This release adds a major re-work to the Gatsby Preview experience! It adds remote Gatsby state management and error handling in WordPress so that WP and Gatsby don't get out of sync during the Preview process.
## 0.5.4
- Force enable WPGraphQL Introspection when WPGatsby is enabled. [WPGraphQL v0.14.0](https://github.com/wp-graphql/wp-graphql/releases/tag/v0.14.0) has Introspection disabled by default with an option to enable it, and Gatsby requires it to be enabled, so WPGatsby force-enables it.

## 0.5.3

- Meta delta syncing was using the same code for posts and users. In many cases this was causing errors when updating usermeta. This code is now scoped to posts only and we will add usermeta delta syncing separately.
- Our composer setup was previously double autoloading

## 0.5.2

- Added a backwards compatibility fix for a regression introduced in v0.4.18 where WPGraphQL::debug() was called. This method is only available in later versions of WPGraphQL, but this plugin currently supports earlier versions

## 0.5.1

- Fixed a typo in the new footer locations 🤦‍♂️ gatbsy should be gatsby
## 0.5.0

### Bug Fixes

- Added support for delta syncing menu locations. This appeared as a bug where updating your menu locations didn't update in Gatsby, but this was actually a missing feature.

## 0.4.18

### Bug Fixes

- The action_monitor post type was registered incorrectly so that it was showing in the rest api, in search, and other places it didn't need to be. This release fixes that. Thanks @jasonbahl!

## 0.4.17

### New Features

-   Added `WPGatsby.arePrettyPermalinksEnabled` to the schema in order to add more helpful error messages to the Gatsby build process.
-   Added a filter `gatsby_trigger_dispatch_args` to filter the arguments passed to `wp_safe_remote_post` when triggering webhooks.

## 0.4.16

### Bug Fixes

It turns out the new feature in the last release could potentially cause many more issues than it presently solves, so it has been disabled as a bug fix. This will be re-enabled within the next couple weeks as we do more testing and thinking on how best to approach sending WP options events to Gatsby.

## 0.4.15

### New Features

-   Non-node root fields (options and settings) are now recorded as an action so Gatsby can inc build when the site title changes for example.

## 0.4.14

### Bug Fixes

-   Making a post into a draft was not previously saving an action monitor post which means posts that became drafts would never be deleted.

## 0.4.13

### Bug Fixes

-   the ContentType.archivePath field was returning an empty string instead of `/` for a homepage archive.

## 0.4.12

### New Features

-   Added temporary `ContentType.archivePath` and `Taxonomy.archivePath` fields to the schema until WPGraphQL supports these fields.

## 0.4.11

### Bug Fixes

-   get_home_url() was being used where get_site_url() should've been used, causing the gql endpoint to not be referenced correctly in some situations. For example when using Bedrock.

## 0.4.10

### Bug Fixes

-   The Preview fix in the last release introduced a new bug where saving a draft at any time would send a webhook to the Preview instance.

## 0.4.9

### Bug Fixes

-   Preview wasn't working properly for new posts that hadn't yet been published or for drafts.

## 0.4.8

Pushing release to WordPress.org

## 0.4.7

### New Features

-   Added a link to the GatsbyJS settings page on how to configure this plugin.

### Bug Fixes

-   Activating this plugin before WPGraphQL was causing PHP errors.

## 0.4.6

Add Wapuu Icons for display in the WordPress.org repo

## 0.4.5

Re-publish with proper package name

## 0.4.4

Testing Github Actions

## 0.4.3

New release to trigger publishing to WordPress.org!

## 0.4.2

### Bug Fixes

-   Previously when a post transitioned from published to draft, it wouldn't be deleted in Gatsby

## 0.4.1

Version bump to add /vendor directory to Git so that Github releases work as WP plugins without running `composer install`. In the future there will be a better release process, but for now this works.

## 0.4.0

### Breaking Changes

-   WPGraphQL was using nav_menu for it's menu relay id's instead of term. WPGQL 0.9.1 changes this from nav_menu to term. This is a breaking change because cache invalidation wont work properly if the id is incorrect. So we move to v0.4.0 so gatsby-source-wordpress-experimental can set 0.4.0 as it's min version and cache invalidation will keep working.

## 0.3.0

### Breaking Changes

-   Updated Relay ids to be compatible with WPGraphQL 0.9.0. See https://github.com/wp-graphql/wp-graphql/releases/tag/v0.9.0 for more info.
-   Bumped min PHP and WP versions

## 0.2.6

### Bug fixes

Fixed an issue where we were trying to access post object properties when we didn't yet have the post.

## 0.2.5

### Bug Fixes

Earlier versions of WPGatsby were recording up to 4 duplicate content saves per content change in WordPress. This release stops that from happening. WPGatsby does garbage collection, so any duplicate actions will be automatically removed from your DB.
