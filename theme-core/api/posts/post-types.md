# Post-Types

This page covers endpoints available for all post types like

* contacts
* groups
* custom post types. Click \[\[here\|Custom post types\]\] for more information.

## Endpoints

CRU~~D~~

* \[\[Create post\]\]: POST /wp-json/dt-posts/v2/{post-type}
* \[\[Get post\]\]: GET /wp-json/dt-posts/{post-type}/v2/post-type/{post\_id}
* \[\[Update post\]\]: POST /wp-json/dt-posts/v2/{post-type}/{post\_id}

List

* \[\[List posts\]\]: GET /wp-json/dt-posts/v2/{post-type}
* \[\[List posts for typeaheads\|list-posts-compact\]\]: GET /wp-json/dt-posts/v2/{post-type}/compact

Comments

* \[\[Get comments\|Post-Comments\]\]: GET /wp-json/dt-posts/v2/{post-type}/{post\_id}/comments
* \[\[Create comment\|Post-Comments\]\]: POST /wp-json/dt-posts/v2/{post-type}/{post\_id}/comments
* \[\[Update comment\|Post-Comments\]\]: POST /wp-json/dt-posts/v2/{post-type}/{post\_id}/comments/{comment\_id}
* \[\[Delete comment\|Post-Comments\]\]: DELETE /wp-json/dt-posts/v2/{post-type}/{post\_id}/comments/{comment\_id}

Activity

* \[\[Get activity\|Post-Activity\]\]: GET /wp-json/dt-posts/v2/{post-type}/{post\_id}/activity
* \[\[Get one activity\|Post-Activity\]\]: GET /wp-json/dt-posts/v2/{post-type}/{post\_id}/activity/{activity\_id}

Shares

* \[\[Get shares\|Post-Sharing\]\]: GET /wp-json/dt-posts/v2/{post-type}/{post\_id}/shares
* \[\[Add shares\|Post-Sharing\]\]: POST /wp-json/dt-posts/v2/{post-type}/{post\_id}/shares
* \[\[Remove shares\|Post-Sharing\]\]: DELETE /wp-json/dt-posts/v2/{post-type}/{post\_id}/shares

Following

* \[\[Get users following\|Post-Following\]\]: GET /wp-json/dt-posts/v2/{post-type}/{post\_id}/following

Settings

* Get settings: GET /wp-json/dt-posts/v2/{post-type}/settings
* Multi\_select values: GET /wp-json/dt-posts/v2/{post-type}/multi-select-values

