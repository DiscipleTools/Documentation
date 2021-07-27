## Here is a sumarry of the tabels D.T uses

### wp_posts
- D.T records like contacts and groups
- The post row contains limited data like: post ID, name, author, creation date
### wp_postmeta
- Stores field data abot the recod
- Example: status, milestones
###  wp_dt_post_user_meta
- D.T custom table
- Stores record data that is only visible to one user (private fields)
- Example: my favorite contacts
### wp_comments
- Stores record comments
### wp_commentmeta
- Stores comment meta like
- Example: reactions
###  wp_dt_share
- D.T custom table
- Stores who a record is shared with (which users have access to a record)
### wp_p2p
- Stores connections to other records
- Example: contact records that form a group's members
### wp_p2pmeta
- Stores p2p meta. Currently unused
### wp_dt_activity_log
- D.T custom table, stores activity on records
- Example: Milestone "praying" selected on July 27 2020 at 7:23pm
### wp_dt_location_grid
- D.T custom table.
- Stores the base location grid project. Used in the location field
- Example: Paris, France, grid_id: 100089652, level: admin2
###  wp_dt_location_grid_meta
- D.T custom table
- Stores extra geocoding data when using a geocoder from mapbox or google
###  wp_dt_notifications
- D.T custom table
- Stores web notifications for user to see when they log in
- Example: You were assigned on contact John Doe
### wp_dt_reports
- D.T custom table
- Stores lightweight events
- Possible example: meeting times
### wp_dt_reportmeta
- D.T custom table
- Store extra information on a report
### wp_dt_movement_log
- D.T custom table
- Stores geocoded event that can more easily be queried
### wp_options
- WP table
- Stores settings and configurations used by D.T
### wp_users
- WP table
- Each user that user the D.T system has a user record
### wp_usermeta
- WP table
- Stores user information
- Example: prefered language


## Tables that D.T does not use:
- wp_links
- wp_term_relationships
- wp_term_taxonomy
- wp_termmeta
- wp_terms
