---
title: How to use API in HiddifyManager project
---

# How to use API in HiddifyManager project

Here is a guide for using the API in HiddifyManager, which comes in two sections: working with normal users and working with admin users.

* To get a list of all users
  
```
GET https://site.com/proxy_path/admin_key/api/v1/user/
```

* To get a specific user

```
  GET https://site.com/proxy_path/admin_key/api/v1/user/?uuid=6ebd2ea8-4d41-48b7-8fc2-7d6570
```

* To create or update a user

```
POST https://site.com/proxy_path/admin_key/api/v1/user/
         {
             "uuid": "6ebd2ea8-4d41-48b7-8fc2-7d6570da30a9",
             "name": "Test",
             "added_by_uuid": "abb4bdb8-732c-4fa6-92e0-6b3fd4bb8450",
             "current_usage_GB": 0,
             "usage_limit_GB": 1,
             "package_days": 900,
             "start_date": null,
             "comment": null,
             "last_online": "1-01-01 00:00:00",
             "last_reset_time": "2023-05-21",
             "mode": "no_reset",
             "telegram_id": null
         }
```
> [!Note]
> The ed25519_private_key and ed25519_public_key fields are optional and will be generated by the system if not available.

* To get all admin users
```
GET https://site.com/proxy_path/admin_key/api/v1/admin/
```
* To get an admin user
```
GET https://site.com/proxy_path/admin_key/api/v1/admin/?uuid=abb4bdb8-732c-4fa6-92e0-6b3fd4bb8450
```
* To create or update admin user
```
POST https://site.com/proxy_path/admin_key/api/v1/admin/
         {
             "uuid": "0749f63d-16c1-4bdf-8d4f-180bcd4cdef6",
             "can_add_admin": false,
             "mode": "agent",
             "name": "Hiddify-Admin",
             "parent_admin_uuid": "abb4bdb8-732c-4fa6-92e0-6b3fd4bb8450",
             "comment": null,
             "telegram_id": null
         }
```
* url format related to the user
```
https://site.com/proxy_path/uuid/
```
* To get the short link of the user's page
```
GET https://site.com/proxy_path/user_uuid/short/
```
* To get user information
```
GET https://site.com/proxy_path/user_uuid/info/
```
* To get the list of Telegram user proxies
```
GET https://site.com/proxy_path/user_uuid/mtproxies/
```
* To get the link of all user configurations
```
GET https://site.com/proxy_path/user_uuid/all-configs/
```