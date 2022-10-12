---
description: Hypermedia As The Engine Of Application State
---

# HATEOAS

Format JSON

```json
{
    "id" : "5wxgYgs41BZoohKMdwrMKj",
    "status" : "ACTIVE",
    "metadata" : {
    "category" : "Architecture",
    "subcategory" : "REST"
    },
    "author" : {
    "id" : "70Wvi8uyl9mFFM4xuVdI5o",
    "name" : "John Smith"
    },
    _"links" : [
        {
        "rel" : "self",
        "href" : "https://api.droga.dev/courses/5wxgYgs41BZoohKMdwrMKj"
        },
        {
        "rel" : "author",
        "href" : "https://api.droga.dev/authors/70Wvi8uyl9mFFM4xuVdI5o"
        }
    ]
}
```

Format HAL

```json
{
    "id" : "5wxgYgs41BZoohKMdwrMKj",
    "status" : "ACTIVE",
    "metadata" : {
    "category" : "Architecture",
    "subcategory" : "REST"
    },
    "_embedded" : {
        "author" : {
            "id" : "70Wvi8uyl9mFFM4xuVdI5o",
            "name" : "John Smith",
            "_links" : {
                "self" : {
                    "href" : "https://api.droga.dev/authors/70Wvi8uyl9mFFM4xuVdI5o"
                    }
                }
            }
        },
        "_links" : {
            "self" : {
                "href" : "https://api.droga.dev/courses/5wxgYgs41BZoohKMdwrMKj"
            }
    }
}
```
