---
title: Dojo API Documentation

language_tabs:
  - ruby

toc_footers:
  - <a href='https://dojo.alphacamp.co/users/1/integrations'>Get your API Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Endpoint URLs

* API Endpoint (Staging): [https://dojo-staging.alphacamp.co](https://dojo-staging.alphacamp.co)
* API Endpoint (Production): [https://dojo.alphacamp.co](https://dojo.alphacamp.co)

# Authentication

* 所有 Request 都必須加上上述的api_key參數，每個 app 用開發者自己的 `api_key`
* 除了登入之外，其他 Request 都必須加上該 app 使用者 `auth_token參數`，下述：

### 登入 POST /api/v1/login
* Parameters:
  * auth_token
  * email
  * password
* Response:
  * 成功 HTTP Code: 200 `{ "message" => "Ok", "auth_token => "XXX", "user_id": 123 }`
  * 失敗 HTTP Code 401 `{ "message => "Failed message" }`

### 登出 POST /api/v1/logout

# Courses API

## 拿 Courses 資料
```json
{
   "courses":[
      {
         "id":"sandbox",
         "url":"https://school.alphacamp.co/courses/sandbox/lessons",
         "name":"測試砂箱 Bootcamp",
         "description":"測試砂箱用",
         "teachers":[
            {
               "id":9,
               "url":"https://school.alphacamp.co/users/9",
               "full_name":"Brian Fang",
               "nickname":"briannfang",
               "email":"ho.fang@gmail.com",
               "avatar_url":"https://www.gravatar.com/avatar/0de7c919becb83686bbba5d25e6f3484"
            },
            {
               "id":1,
               "url":"https://school.alphacamp.co/users/1",
               "full_name":"文鈿 張",
               "nickname":"ihower",
               "email":"ihower@alphacamp.co",
               "avatar_url":"https://www.gravatar.com/avatar/a33a07825f8dc3fbd69a7ecf2ecc88c6"
            }
         ],
         "start_on":"2015-01-01",
         "end_on":"2015-12-31",
         "updated_at":"2015-01-20T21:53:01.972Z",
         "created_at":"2015-01-16T05:08:33.912Z"
      },
      {
         "id":"web-bootcamp-4",
         "url":"https://school.alphacamp.co/courses/web-bootcamp-4/lessons",
         "name":"網站開發工程師實戰營",
         "description":"",
         "teachers":[
            {
               "id":1,
               "url":"https://school.alphacamp.co/users/1",
               "full_name":"文鈿 張",
               "nickname":"ihower",
               "email":"ihower@alphacamp.co",
               "avatar_url":"https://www.gravatar.com/avatar/a33a07825f8dc3fbd69a7ecf2ecc88c6"
            }
         ],
         "start_on":"2015-03-09",
         "end_on":"2015-05-17",
         "updated_at":"2015-01-20T21:50:23.478Z",
         "created_at":"2014-12-24T10:26:31.596Z"
      }
   ],
   "paging":{
      "current_page":1,
      "total_pages":1,
      "per_page":25,
      "next_url":null,
      "previous_url":null
   }
}
```
* `GET /api/v1/courses`
* 請看右欄 JSON Example


## 拿特定 Course 完整資料，包括 Pages, Sections 和 Lessons

```json
{
   "course":{
      "id":"sandbox",
      "url":"https://school.alphacamp.co/courses/sandbox/lessons",
      "name":"測試砂箱 Bootcamp",
      "description":"測試砂箱用",
      "teachers":[
         {
            "id":9,
            "url":"https://school.alphacamp.co/users/9",
            "full_name":"Brian Fang",
            "nickname":"briannfang",
            "email":"ho.fang@gmail.com",
            "avatar_url":"https://www.gravatar.com/avatar/0de7c919becb83686bbba5d25e6f3484"
         },
         {
            "id":1,
            "url":"https://school.alphacamp.co/users/1",
            "full_name":"文鈿 張",
            "nickname":"ihower",
            "email":"ihower@alphacamp.co",
            "avatar_url":"https://www.gravatar.com/avatar/a33a07825f8dc3fbd69a7ecf2ecc88c6"
         }
      ],
      "start_on":"2015-01-01",
      "end_on":"2015-12-31",
      "updated_at":"2015-01-20T21:53:01.972Z",
      "created_at":"2015-01-16T05:08:33.912Z"
   },
   "pages":[
      {
         "id":4,
         "name":"近期活動",
         "type":"content",
         "url":"https://school.alphacamp.co/courses/sandbox/pages/4"
      },
      {
         "id":5,
         "name":"Blog 連結",
         "type":"url",
         "url":"https://blog.alphacamp.co/"
      }
   ],
   "syllabus":[
      {
         "section":{
            "id":2,
            "name":"Week 1: 認識 ALPHA Camp",
            "description":""
         },
         "lessons":[
            {
               "id":3,
               "url":"https://school.alphacamp.co/courses/sandbox/lessons/3",
               "name":"第一課-認識 ALPHA Camp",
               "description":"",
               "created_at":"2015-01-16T05:09:13.476Z",
               "updated_at":"2015-01-16T06:45:35.493Z"
            },
            {
               "id":4,
               "url":"https://school.alphacamp.co/courses/sandbox/lessons/4",
               "name":"第二課-認識校園",
               "description":"",
               "created_at":"2015-01-16T05:11:32.903Z",
               "updated_at":"2015-01-16T05:11:32.903Z"
            }
         ]
      },
      {
         "section":{
            "id":3,
            "name":"Week2: 認識創業",
            "description":""
         },
         "lessons":[
            {
               "id":5,
               "url":"https://school.alphacamp.co/courses/sandbox/lessons/5",
               "name":"如何募資",
               "description":"",
               "created_at":"2015-01-16T07:27:52.050Z",
               "updated_at":"2015-01-16T07:29:15.425Z"
            },
            {
               "id":7,
               "url":"https://school.alphacamp.co/courses/sandbox/lessons/7",
               "name":"如何招聘",
               "description":"",
               "created_at":"2015-01-16T07:28:43.317Z",
               "updated_at":"2015-01-16T07:28:48.472Z"
            },
            {
               "id":6,
               "url":"https://school.alphacamp.co/courses/sandbox/lessons/6",
               "name":"如何打造人見人愛的產品",
               "description":"",
               "created_at":"2015-01-16T07:28:27.219Z",
               "updated_at":"2015-01-16T07:28:27.219Z"
            },
            {
               "id":8,
               "url":"https://school.alphacamp.co/courses/sandbox/lessons/8",
               "name":"創業與人生",
               "description":"",
               "created_at":"2015-01-16T07:29:03.512Z",
               "updated_at":"2015-01-16T07:29:03.512Z"
            }
         ]
      }
   ]
}
```


* `GET /api/v1/courses/{course_id}`
* 請看右欄 JSON Example

<aside class="notice">
page 有兩種類型，一種是有內文的放在 Dojo 上 (type 是 content)，一種是外部連結(type 是 url)。外部連結可以直接開 webview 沒有權限問題!
</aside>


# Users API

## 取得個人資料 GET /api/v1/me

```json
{
  "id": 109,
  "email": "yangliyi@hotmail.com",
  "nickname": "LY",
  "fullname": "Yang Li-yi",
  "bio": "example bio",
  "website": "https://medium.com/@yangliyi",
  "phone": "0933123456",
  "avatar": "http://s3-ap-northeast-1.amazonaws.com/alphacamp-development/users/avatars/000/000/109/original/11146379_938898942809351_7576090202362115225_o.jpg?1440984709"
}
```

* 拿 user 資料
  * `GET /api/v1/me`
  * 請看右欄 JSON Example
* Response
  * 失敗 HTTP Code: 401 `{ "message" => "Failed" }`

## 更新個人資料 PATCH /api/v1/me

### Parameters

Name | Type
------- | -----------
email | string
nickname | string
fullname | string
bio | text
website | string
phone | string
avatar | image

### Parameters
* 成功 HTTP Code: 200 `{ "message" => "Successfully updated", "user_id": 123 }`
* 失敗 HTTP Code: 400 `{ "message" => "Failed" }`

