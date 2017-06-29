
## Status_Types 

| id |   Name                 | Comments                    |
|----|------------------------|-----------------------------|
| 1  |  recieveed             |                             |
| 2  |  evaluation            |                             |
| 3  |  pending CAF approval  |                             |
| 4  |  on hold               |                             |
| 5  |  engineering           |                             |
| 6  |  provisioning          |                             |
| 7  |  testing               |                             |
| 8  |  ready                 |                             |
| 9  |  active                |                             |
| 10 |  pending disconnect    |                             |
| 11 |  disconnected          |                             |
| 12 |  withdrawn             |                             |
| 13 |  customer accepted     |                             |
| 14 |  customer rejected CAF |                             |
| 15 |  customer manual ROM   |
| 16 |  ROM complete          | n |


## Order Table
```ruby

create_table "orders", force :cascade do |t|
    t.integer "updated_by_user_id",   limit:4
    t.string "order_number",          limit: 128 default: 0
    t.datetime "order_date"
    t.datetime "update_updated_time"
    t.integer "status_id"         ,   limit:4
    t.string "status_updated_by_username"
    t.datetime "status_updated_date"
end
```

