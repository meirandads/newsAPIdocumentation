API Documentation

Overview

API ini menyediakan akses untuk mendapatkan daftar artikel berita dan detailnya berdasarkan parameter tertentu. API ini mendukung format JSON untuk input dan output data.

Base URL

https://article2-199228555553.asia-southeast2.run.app

Endpoint List

1. Get All News

Endpoint: /news

Method: GET

Deskripsi: Mendapatkan daftar artikel berita berdasarkan parameter tertentu.

Request Parameters

Parameter

Tipe

Deskripsi

Contoh

country

string

Kode negara artikel berita

us

category

string

Kategori artikel berita

business

Contoh Request

GET /news?country=us&category=business HTTP/1.1
Host: article2-199228555553.asia-southeast2.run.app

Response

Status Code: 200 OK

Response Body:

{
  "articles": [
    {
      "id": 1000,
      "title": "Coca-Cola just weakened its goal to reduce single-use plastics - The Washington Post",
      "description": "The company said it will shift its focus to plastic recycling...",
      "url": "https://www.washingtonpost.com/climate-environment/2024/12/03/coca-cola-plastic-sustainability-goal/",
      "image": "https://www.washingtonpost.com/wp-apps/imrs.php?...",
      "category": "business",
      "country": "us",
      "publishedAt": "2024-12-03T10:00:00Z"
    }
  ],
  "status": "success"
}

Status Code: 404 Not Found

Error Response:

{
  "message": "No articles found for the given parameters.",
  "status": "error"
}

2. Get News by ID

Endpoint: /news/{id}

Method: GET

Deskripsi: Mendapatkan detail artikel berita berdasarkan ID.

Path Parameters

Parameter

Tipe

Deskripsi

Contoh

id

int

ID unik dari artikel berita

1000

Contoh Request

GET /news/1000 HTTP/1.1
Host: article2-199228555553.asia-southeast2.run.app


Response

Status Code: 200 OK

Response Body:

{
  "article": {
    "id": 1000,
    "title": "Tim Cook Wants Apple to Literally Save Your Life - WIRED",
    "description": "Much as the CEO seems awestruck by AI...",
    "url": "https://www.wired.com/story/big-interview-tim-cook-wants-apple-to-literally-save-your-life/",
    "image": "https://media.wired.com/photos/...",
    "category": "technology",
    "country": "us",
    "publishedAt": "2024-12-03T12:00:00Z"
  },
  "status": "success"
}

Status Code: 404 Not Found

Error Response:

{
  "message": "The requested URL was not found on the server.",
  "status": "error"
}

Rate Limits

Limit: 300 requests per minute.

Jika melebihi batas:

Status Code: 429 Too Many Requests

Response Body:

{
  "message": "Rate limit exceeded. Please try again later.",
  "status": "error"
}

