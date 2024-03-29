# List of Endpoints

This page covers endpoints available for all post types like

* contacts
* groups
* custom post types. Click [here](../customization/custom-post-types.md) for more information.

## Endpoints

CRU~~D~~

* [Create post](create-post.md): POST /wp-json/dt-posts/v2/{post-type}
* [Get post](get-post.md): GET /wp-json/dt-posts/{post-type}/v2/post-type/{post\_id}
* [Update post](update-post.md): POST /wp-json/dt-posts/v2/{post-type}/{post\_id}

List

* [List posts](list-query.md): GET /wp-json/dt-posts/v2/{post-type}
* [List posts for Typeaheads](list-posts-compact.md): GET /wp-json/dt-posts/v2/{post-type}/compact

Comments

* [Get comments](post-comments.md): GET /wp-json/dt-posts/v2/{post-type}/{post\_id}/comments
* [Create comment](post-comments.md): POST /wp-json/dt-posts/v2/{post-type}/{post\_id}/comments
* [Update comment](post-comments.md): POST /wp-json/dt-posts/v2/{post-type}/{post\_id}/comments/{comment\_id}
* [Delete comment](post-comments.md): DELETE /wp-json/dt-posts/v2/{post-type}/{post\_id}/comments/{comment\_id}

Activity

* [Get activity](post-activity.md): GET /wp-json/dt-posts/v2/{post-type}/{post\_id}/activity
* [Get one activity](post-activity.md): GET /wp-json/dt-posts/v2/{post-type}/{post\_id}/activity/{activity\_id}

Shares

* [Get shares](post-sharing.md): GET /wp-json/dt-posts/v2/{post-type}/{post\_id}/shares
* [Add shares](post-sharing.md): POST /wp-json/dt-posts/v2/{post-type}/{post\_id}/shares
* [Remove shares](post-sharing.md): DELETE /wp-json/dt-posts/v2/{post-type}/{post\_id}/shares

Following

* [Get users following](post-following.md): GET /wp-json/dt-posts/v2/{post-type}/{post\_id}/following

Settings

* [Get settings](post-settings.md): GET /wp-json/dt-posts/v2/{post-type}/settings
* Multi\_select values: GET /wp-json/dt-posts/v2/{post-type}/multi-select-values

Global Search

* [Global search](global-search.md): GET /wp-json/dt-posts/v2/posts/search/advanced_search
