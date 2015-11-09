[RESTFUL API LÀ GÌ](https://viblo.asia/khanhhd/posts/l5y8Rro9Mob3)
[VIDEO REST APIs CONCEPT](https://www.youtube.com/watch?v=RTjd1nwvlj4)
![REST API](https://impythonist.files.wordpress.com/2015/07/rstapi.jpg)
![REST API](http://aci-troubleshooting-book.readthedocs.org/en/latest/_images/rest-api.jpg)

EX:
**Request**

```GET /
Accept: application/json
```

**Response**

```200 OK
Content-Type: application/json

{
    "id": 1,
    "news": [
        {
            "id": 1,
            "title": "HOT GIRL",
            "contain": "list hot girl",
            "ctime": "11/11/2011",
            "images": ["girl1.jpg", "girl2.jpg"]
        },
        {
            "id": 2,
            "title": "HOT BOY",
            "contain": "list hot boy",
            "ctime": "12/12/2012"
        }
    ]
}
```
