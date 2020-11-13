---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - json

toc_footers:
  - <a href='https://ambsuperapi.com/profile'>AMB SuperAPI Agent Profile Page</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: false

code_clipboard: true
---

# Introduction

**AMB SuperAPI** is designed around RESTFUL API. Our API is made for everyone to be able to read and predictable oriented URLs.The AMB SuperAPI allows you to integrate with the various game providers around the world without handling every risk during the integration of the game provider by yourself and **super simple to use**..

**After Start**

When you request the API endpoint these need to use a valid API Key. You can get your API key from the [AMB SuperAPI Agent Profile Page](https://ambsuperapi.com/profile)

# Authentication

An **API Key** is required to be sent as a part of every request, In the form of [Basic Authentication](https://swagger.io/docs/specification/authentication/basic-authentication/#:~:text=Basic%20authentication%20is%20a%20simple,55w0rd%20the%20client%20would%20send)
in the request header,

such as `Authorization: Basic abcdefghijklmnop`

So, The `abcdefghijklmnop` it comes from [Base64-encoded](https://en.wikipedia.org/wiki/Base64) of string `agent_username:x-api-key`.

**that means the username of basic auth is an `agent_username` and the password is an `x-api-key`**

If you do not have an API Key, you can easily generate one by heading over to the [AMB SuperAPI Agent Profile Page](https://ambsuperapi.com/profile)

![image](https://user-images.githubusercontent.com/4927368/95018045-22417980-0687-11eb-89d4-6050a3d2fcef.png)

**API Key related error response**

If an API Key is missing, malformed, or invalid, you will receive a `403 Unauthorised response code` and the following JSON response:

<aside class="notice">
{
    "message": "Unauthorized",
    "timestamp": "2020-10-04T14:12:33.013Z",
    "path": "/member"
}
</aside>
```json
```

# API Referance

## Category Lists

| Value      | Description |
| ---------- | ----------- |
| EGAMES     | Games Slot  |
| LIVECASINO | Live Casino |
| SPORT      | Sportbook   |

## Product Lists

### Games Slot

| Product ID | Product Name    | Description     |
| ---------- | --------------- | --------------- |
| PGSOFT     | PG Soft         | PG Soft         |
| SLOTXO     | Slotxo          | Slotxo          |
| PPSLOT     | Pragmatic Play  | Pragmatic Play  |
| ASKMEBET   | Habanero        | Habanero        |
| HABANERO   | Spade Gaming    | Spade Gaming    |
| SPADE      | Spade Gaming    | Spade Gaming    |
| MICRO      | Micro Gamingg   | Micro Gamingg   |
| SIMPLEPLAY | Simple Play     | Simple Play     |
| ICONIC     | Iconic Gaming   | Iconic Gaming   |
| MEGA       | Mega888         | Mega888         |
| XIN        | Xin Gaming      | Xin Gaming      |
| LIVE22     | Live22          | Live22          |
| GAMATRON   | Gamatron        | Gamatron        |
| ALLWAYSPIN | Allwayspin      | Allwayspin      |
| FUN        | Fun Gaming      | Fun Gaming      |
| EURASIAN   | Eurasian Gaming | Eurasian Gaming |
| AMBPOKER   | Ambpoker        | Ambpoker        |
| JDB        | JDB             | JDB             |
| WAZDAN     | Wazdan          | Wazdan          |
| EPICWIN    | Epicwin         | Epicwin         |
| EVOPLAY    | Evoplay         | Evoplay         |
| ENDORPHINA | Endorphina      | Endorphina      |
| CQ9        | CQ9             | CQ9             |
| KAGAME     | KA Gaming       | KA Gaming       |
| JILI       | Jili            | Jili            |
| JOKER      | Joker123        | Joker123        |
| MANNA      | Mannaplay       | Mannaplay       |

### Live Casino

| Product ID | Product Name   | Description    |
| ---------- | -------------- | -------------- |
| SEXY       | Sexy Gaming    | Sexy Gaming    |
| PPCASINO   | Pragmatic Play | Pragmatic Play |
| BIGGAME    | Big Gaming     | Big Gaming     |
| DREAM      | Dream Gaming   | Dream Gaming   |
| WM         | WM Casino      | WM Casino      |
| BETGAME    | BetgamesTV     | BetgamesTV     |
| GCLUB      | Royal GClub    | Royal GClub    |
| EBET       | Ebet           | Ebet           |
| ALLBET     | AllBet         | AllBet         |
| AGGAME     | Asia Gaming AG | Asia Gaming AG |
| PRETTY     | Pretty Gaming  | Pretty Gaming  |
| SAGAME     | SA Gaming      | SA Gaming      |

### Sportbook

| Product ID | Product Name | Description |
| ---------- | ------------ | ----------- |
| SBO        | Sbobet       | Sbobet      |
| IBC        | IBC          | IBC         |
| BBIN       | BBIN         | BBIN        |
| WBET       | WBET         | WBET        |
| TFGAME     | TF Gaming    | TF Gaming   |
| IAE        | IAEsports    | IAEsports   |

# API

## Overview

**Let's play**

1. First, Create a member/gambler on the product that you want in the above [Product List](#product-lists)
2. Deposit some credit to member for playing the game
3. Login and get a URL to play the game and turn into a millionire
4. Withdraw

## List Games `GET`

> JSON response example:

```json
{
  "reqId": "91ffb817-1f8e-4608-a86d-472dddc2eed7",
  "code": 0,
  "message": "Success",
  "data": {
    "games": [],
    "status": "SUCCESS"
  }
}
```
### HTTP Request

`GET {{ API_URL }}/games?productId={{ productId }}`

### Authorization

Authorization: Basic `Base64({{ agent_username }}:{{ x-api-key }})`

### Content Type

Type: `application/json`

### Parameter Description

| Property    | Type   | Compulsory | Description                                                        |
| ----------- | ------ | ---------- | ------------------------------------------------------------------ |
| `productId` | string | Y          | Product ID (Ref. [Product List](#product-lists)) (Example : `PRETTY`) |

## Create Member `POST`

> Request Body

```json
{
  "username": "u1",
  "productId": "PRETTY"
}
```

> JSON response example:

```json
{
  "reqId": "08bbf59d-5619-4c73-ad47-510292dee323",
  "data": {
    "username": "u1",
    "currency": "THB",
    "status": "SUCCESS"
  }
}
```
### HTTP Request

`POST {{ API_URL }}member`

### Authorization

Authorization: Basic `Base64({{ agent_username }}:{{ x-api-key }})`

### Content Type

Type: `application/json`

### Parameter Description

Create a Member also know as Gambler in whatever product

| Property    | Type   | Compulsory | Description                                                        |
| ----------- | ------ | ---------- | ------------------------------------------------------------------ |
| `username`  | string | Y          | Member username                                                    |
| `productId` | string | Y          | Product ID (Ref. [Product List](#product-lists)) (Example : `PRETTY`) |

## Get Balance `GET`

> JSON response example:

```json
{
  "reqId": "4a597d2c-1ac8-413b-aaa7-a673b4939494",
  "code": 0,
  "message": "Success",
  "data": {
    "balance": "10000",
    "status": "SUCCESS",
    "username": "u1"
  }
}
```
### HTTP Request

`GET {{ API_URL }}/balance?username={{ username }}&productId={{ productId }}`


### Authorization

Authorization: Basic `Base64({{ agent_username }}:{{ x-api-key }})`

### Content Type

Type: `application/json`

### Parameter Description

| Property    | Type   | Compulsory | Description                                                        |
| ----------- | ------ | ---------- | ------------------------------------------------------------------ |
| `username`  | string | Y          | Member username                                                    |
| `productId` | string | Y          | Product ID (Ref. [Product List](#product-lists)) (Example : `PRETTY`) |

## Deposit `POST`

> Request Body

```json
{
  "username": "u1",
  "amount": "1.00",
  "transactionRef": "{{ transactionRef }}",
  "productId": "PRETTY"
}
```

> JSON response example:

```json
{
  "reqId": "e56ab2e2-8a40-4fd9-8639-339130d29ad4",
  "code": 0,
  "message": "Success",
  "data": {
    "amount": "10000",
    "balance": "10001",
    "status": "SUCCESS",
    "txId": "u1ddne1605072101",
    "username": "u1",
    "beforeBalance": "10000.00"
  }
}
```

### HTTP Request

`POST {{ API_URL }}/deposit`

### Authorization

Authorization: Basic `Base64({{ agent_username }}:{{ x-api-key }})`

### Content Type

Type: `application/json`

### Parameter Description

| Property         | Type   | Compulsory | Description                                                        |
| ---------------- | ------ | ---------- | ------------------------------------------------------------------ |
| `username`       | string | Y          | Member username                                                    |
| `amount`         | string | Y          | Amount to deposit                                                  |
| `transactionRef` | string | Y          | Unique transaction ref                                             |
| `productId`      | string | Y          | Product ID (Ref. [Product List](#product-lists)) (Example : `PRETTY`) |

## Login `POST`

> Request Body

```json
{
  "username": "u1",
  "productId": "PRETTY",
  "gameCode": "BAC",
  "isMobileLogin": true
}
```

> JSON response example:

```json
{
  "reqId": "5557191a-4421-4753-a757-8ca7b45828dc",
  "code": 0,
  "message": "Success",
  "data": {
    "url": "http://",
    "username": "u1"
  }
}
```

### HTTP Request

`POST {{ API_URL }}/logIn`

### Authorization

Authorization: Basic `Base64({{ agent_username }}:{{ x-api-key }})`

### Content Type

Type: `application/json`

### Parameter Description

| Property        | Type    | Compulsory | Description                                                        |
| --------------- | ------- | ---------- | ------------------------------------------------------------------ |
| `username`      | string  | Y          | Member username                                                    |
| `productId`     | string  | Y          | Product ID (Ref. [Product List](#product-lists)) (Example : `PRETTY`) |
| `gameCode`      | string  | Y          | Game code of product (Example : BAC)                               |
| `isMobileLogin` | boolean | Y          | Mobile Mode (Example : true)                                       |

## Withdraw `POST`

> Request Body

```json
{
  "username": "u1",
  "amount": "1.00",
  "transactionRef": "{{ transactionRef }}",
  "productId": "PRETTY"
}
```

> JSON response example:

```json
{
  "reqId": "485a1fe0-4974-46e1-92f5-2130c9d74743",
  "code": 0,
  "message": "Success",
  "data": {
    "amount": "1000",
    "balance": "9001",
    "status": "SUCCESS",
    "txId": "u1sllz1605072697",
    "username": "u1",
    "beforeBalance": "10001.00"
  }
}
```

### HTTP Request

`POST {{ API_URL }}/withdraw`

### Authorization

Authorization: Basic `Base64({{ agent_username }}:{{ x-api-key }})`

### Content Type

Type: `application/json`

### Parameter Description

| Property         | Type     | Compulsory | Description                                                        |
| ---------------- | -------- | ---------- | ------------------------------------------------------------------ |
| `username`       | string | Y          | Member username                                                    |
| `amount`         | string | Y          | Amount to deposit                                                  |
| `transactionRef` | string | Y          | Unique transaction ref                                             |
| `productId`      | string | Y          | Product ID (Ref. [Product List](#product-lists)) (Example : `PRETTY`) |

## Update Member Password `PATCH`

<aside class="notice">Optional API: Product Slotxo only</aside>

> Request Body

```json
{
  "username": "u1",
  "productId": "SLOTXO",
  "password": "testp1234"
}
```

> JSON response example:

```json
{
    "reqId": "0ffe1434-c931-4ea8-a430-c7fac8bf5a96",
    "code": 0,
    "message": "Success",
    "data": {
        "memberAlias": "TFPF.000ful499"
    }
}
```

### HTTP Request

`PATCH {{ API_URL }}/member`

### Authorization

Authorization: Basic `Base64({{ agent_username }}:{{ x-api-key }})`

### Content Type

Type: `application/json`

### Parameter Description

| Property         | Type     | Compulsory | Description | |
| ---------------- | -------- | ---------- | -------------- | -- |
| `username`       | string | Y          | Member username | |
| `productId`      | string | Y          | Product ID of **SLOTXO** | `Slotxo only`|
| `password`       | string | Y          | password | |

## Get Member Alias `GET`

<aside class="notice">Optional API: Product Slotxo only</aside>

> JSON response example:

```json
{
    "reqId": "44b308ec-4235-4c47-82e6-8d370dbf1fc9",
    "code": 0,
    "message": "Success",
    "data": {
        "memberAlias": "TFPF.000ful499"
    }
}
```
### HTTP Request

`GET {{ API_URL }}/member/{{ username }}/alias?productId={{ productId }}`


### Authorization

Authorization: Basic `Base64({{ agent_username }}:{{ x-api-key }})`

### Content Type

Type: `application/json`

### Parameter Description

| Property    | Type   | Compulsory | Description | |
| ----------- | ------ | ---------- | ---------- | -- |
| `username`       | string | Y          | Member username | |
| `productId` | string | Y          | Product ID of **SLOTXO** | `Slotxo only`|