{
  "collection": {
    "info": {
      "_postman_id": "d3c44ec2-0f5b-4fcc-af42-bda702d5d95f",
      "name": "Demoshopping",
      "schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json",
      "updatedAt": "2025-07-26T07:14:40.000Z",
      "createdAt": "2025-07-22T17:03:02.000Z",
      "lastUpdatedBy": "44723816",
      "uid": "44723816-d3c44ec2-0f5b-4fcc-af42-bda702d5d95f"
    },
    "item": [
      {
        "name": "Login",
        "item": [
          {
            "name": "Логин",
            "id": "f5b56488-d904-4b4f-a101-d5b18d5aa5ca",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "POST",
              "header": [],
              "body": {
                "mode": "raw",
                "raw": "{\r\n  \"username\": \"{{username}}\",\r\n  \"password\": \"{{password}}\"\r\n}",
                "options": {
                  "raw": {
                    "language": "json"
                  }
                }
              },
              "url": {
                "raw": "{{url_shop}}/login",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "login"
                ]
              }
            },
            "response": [],
            "uid": "44723816-f5b56488-d904-4b4f-a101-d5b18d5aa5ca"
          }
        ],
        "id": "00b1e3a9-7bee-40bc-815d-ad6322796bcb",
        "uid": "44723816-00b1e3a9-7bee-40bc-815d-ad6322796bcb"
      },
      {
        "name": "Products",
        "item": [
          {
            "name": "Просмотр всех товаров",
            "id": "70aa4144-69fa-482c-8c20-87ea7d4828c2",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "GET",
              "header": [],
              "url": {
                "raw": "{{url_shop}}/products",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "products"
                ]
              }
            },
            "response": [],
            "uid": "44723816-70aa4144-69fa-482c-8c20-87ea7d4828c2"
          },
          {
            "name": "Добавление нового продукта",
            "event": [
              {
                "listen": "test",
                "script": {
                  "id": "89c8f4a0-dbdf-42f4-9814-796c90022dd3",
                  "exec": [
                    "const response = pm.response.text(); // Changed to text() to handle HTML response\r",
                    "\r",
                    "const productID = response.match(/ID: (\\d+)/)[1]; // Extracting ID using regex\r",
                    "\r",
                    "pm.collectionVariables.set(\"productID\", productID);\r",
                    "\r",
                    "console.log(\"Save productID:\", productID);\r",
                    ""
                  ],
                  "type": "text/javascript",
                  "packages": {

                  }
                }
              }
            ],
            "id": "2c97ac69-4cfb-40d7-a66a-ecab6f894cf1",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "POST",
              "header": [],
              "body": {
                "mode": "raw",
                "raw": "{\r\n  \"name\": \"Example Product\",\r\n  \"description\": \"This is an example product.\",\r\n  \"price\": 100,\r\n  \"category\": \"Electronics\",\r\n  \"manufacturer\": \"Example Manufacturer\",\r\n  \"imageUrl\": \"http://example.com/image.jpg\",\r\n  \"freeShipping\": true\r\n}",
                "options": {
                  "raw": {
                    "language": "json"
                  }
                }
              },
              "url": {
                "raw": "{{url_shop}}/add-product",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "add-product"
                ]
              }
            },
            "response": [],
            "uid": "44723816-2c97ac69-4cfb-40d7-a66a-ecab6f894cf1"
          },
          {
            "name": "Поиск продукта по ID",
            "event": [
              {
                "listen": "prerequest",
                "script": {
                  "id": "6aa10d5d-ee23-4e22-84c7-ddf183e74e6c",
                  "exec": [
                    ""
                  ],
                  "type": "text/javascript",
                  "packages": {

                  }
                }
              }
            ],
            "id": "ac2d4c79-0835-473d-8338-648347728cb6",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "GET",
              "header": [],
              "url": {
                "raw": "{{url_shop}}/products/id/{{productID}}",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "products",
                  "id",
                  "{{productID}}"
                ]
              }
            },
            "response": [],
            "uid": "44723816-ac2d4c79-0835-473d-8338-648347728cb6"
          },
          {
            "name": "Полное обновление товара по ID",
            "id": "27bdaf98-f384-45c5-a3bd-858c637f4e85",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "PUT",
              "header": [],
              "body": {
                "mode": "raw",
                "raw": "{\r\n  \"id\": 0,\r\n  \"name\": \"string\",\r\n  \"description\": \"string\",\r\n  \"price\": 0,\r\n  \"category\": \"string\",\r\n  \"manufacturer\": \"string\",\r\n  \"imageUrl\": \"string\",\r\n  \"freeShipping\": true\r\n}",
                "options": {
                  "raw": {
                    "language": "json"
                  }
                }
              },
              "url": {
                "raw": "{{url_shop}}/products/id/{{productID}}",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "products",
                  "id",
                  "{{productID}}"
                ]
              }
            },
            "response": [],
            "uid": "44723816-27bdaf98-f384-45c5-a3bd-858c637f4e85"
          },
          {
            "name": "Частичное обновление товара по ID",
            "id": "1e8e0952-f7d9-4013-a43c-84ea7f494164",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "PATCH",
              "header": [],
              "body": {
                "mode": "raw",
                "raw": "{\r\n  \"name\": \"string\",\r\n  \"description\": \"string\",\r\n  \"price\": 0,\r\n  \"category\": \"string\",\r\n  \"manufacturer\": \"string\",\r\n  \"imageUrl\": \"string\",\r\n  \"freeShipping\": true\r\n}",
                "options": {
                  "raw": {
                    "language": "json"
                  }
                }
              },
              "url": {
                "raw": "{{url_shop}}/products/id/{{productID}}",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "products",
                  "id",
                  "{{productID}}"
                ]
              }
            },
            "response": [],
            "uid": "44723816-1e8e0952-f7d9-4013-a43c-84ea7f494164"
          },
          {
            "name": "Удаление товара по ID",
            "id": "7faf99fa-8afe-4615-a70d-c073d3ff0624",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "DELETE",
              "header": [],
              "url": {
                "raw": "{{url_shop}}/products/id/{{productID}}",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "products",
                  "id",
                  "{{productID}}"
                ]
              }
            },
            "response": [],
            "uid": "44723816-7faf99fa-8afe-4615-a70d-c073d3ff0624"
          },
          {
            "name": "Поиск по категории",
            "id": "30fb4c79-13a9-4e29-98b5-ba6d6f1cb34c",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "GET",
              "header": [],
              "url": {
                "raw": "{{url_shop}}/products/FindByCategory?category=Watches",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "products",
                  "FindByCategory"
                ],
                "query": [
                  {
                    "key": "category",
                    "value": "Laptops",
                    "disabled": true
                  },
                  {
                    "key": "category",
                    "value": "Phones",
                    "type": "text",
                    "disabled": true
                  },
                  {
                    "key": "category",
                    "value": "Watches",
                    "type": "text"
                  }
                ]
              }
            },
            "response": [],
            "uid": "44723816-30fb4c79-13a9-4e29-98b5-ba6d6f1cb34c"
          },
          {
            "name": "Поиск товаров с бесплатной доставкой",
            "id": "396d6c86-1ee7-48bf-bb44-7aac3ccd3835",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "GET",
              "header": [],
              "body": {
                "mode": "raw",
                "raw": "",
                "options": {
                  "raw": {
                    "language": "text"
                  }
                }
              },
              "url": {
                "raw": "{{url_shop}}/products/FindByShipping?freeShipping=false",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "products",
                  "FindByShipping"
                ],
                "query": [
                  {
                    "key": "freeShipping",
                    "value": "true",
                    "disabled": true
                  },
                  {
                    "key": "freeShipping",
                    "value": "false",
                    "type": "text"
                  }
                ]
              }
            },
            "response": [],
            "uid": "44723816-396d6c86-1ee7-48bf-bb44-7aac3ccd3835"
          },
          {
            "name": "Поиск товара по производителю",
            "id": "f610ae5c-c0d5-41cd-a6d7-6d8021ce3c7f",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "GET",
              "header": [],
              "url": {
                "raw": "{{url_shop}}/products/FindByManufacturer?manufacturer=Apple",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "products",
                  "FindByManufacturer"
                ],
                "query": [
                  {
                    "key": "manufacturer",
                    "value": "Apple",
                    "type": "text"
                  },
                  {
                    "key": "manufacturer",
                    "value": "Xiaomi",
                    "type": "text",
                    "disabled": true
                  },
                  {
                    "key": "manufacturer",
                    "value": "Huawei",
                    "type": "text",
                    "disabled": true
                  },
                  {
                    "key": "manufacturer",
                    "value": "Samsung",
                    "type": "text",
                    "disabled": true
                  }
                ]
              }
            },
            "response": [],
            "uid": "44723816-f610ae5c-c0d5-41cd-a6d7-6d8021ce3c7f"
          },
          {
            "name": "Фильтрация списка продуктов",
            "id": "bf584a23-3787-49ea-a4b5-12ae57eccfcb",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "GET",
              "header": [],
              "url": {
                "raw": "{{url_shop}}/products/filter?category=Laptops&manufacturer=Xiaomi&freeShipping=true&minPrice=1&maxPrice=1000",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "products",
                  "filter"
                ],
                "query": [
                  {
                    "key": "category",
                    "value": "Phones",
                    "type": "text",
                    "disabled": true
                  },
                  {
                    "key": "category",
                    "value": "Watches",
                    "type": "text",
                    "disabled": true
                  },
                  {
                    "key": "category",
                    "value": "Laptops"
                  },
                  {
                    "key": "manufacturer",
                    "value": "Apple",
                    "type": "text",
                    "disabled": true
                  },
                  {
                    "key": "manufacturer",
                    "value": "Huawei",
                    "type": "text",
                    "disabled": true
                  },
                  {
                    "key": "manufacturer",
                    "value": "Xiaomi"
                  },
                  {
                    "key": "manufacturer",
                    "value": "Samsung",
                    "type": "text",
                    "disabled": true
                  },
                  {
                    "key": "freeShipping",
                    "value": "true"
                  },
                  {
                    "key": "freeShipping",
                    "value": "false",
                    "disabled": true
                  },
                  {
                    "key": "minPrice",
                    "value": "1"
                  },
                  {
                    "key": "maxPrice",
                    "value": "1000"
                  }
                ]
              }
            },
            "response": [],
            "uid": "44723816-bf584a23-3787-49ea-a4b5-12ae57eccfcb"
          }
        ],
        "id": "d4fc0b16-ee68-45e9-9b72-f353ad0ca4f9",
        "event": [
          {
            "listen": "prerequest",
            "script": {
              "id": "4ffd5ea0-5b05-48fc-8d07-6be0719c025f",
              "type": "text/javascript",
              "packages": {

              },
              "exec": [
                ""
              ]
            }
          },
          {
            "listen": "test",
            "script": {
              "id": "69ee79f2-7b21-49b9-8024-315968390306",
              "type": "text/javascript",
              "packages": {

              },
              "exec": [
                ""
              ]
            }
          }
        ],
        "uid": "44723816-d4fc0b16-ee68-45e9-9b72-f353ad0ca4f9"
      },
      {
        "name": "Carts",
        "item": [
          {
            "name": "Добавление товара в корзину",
            "id": "b309454d-3081-4f5e-b018-89038a2dda80",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "POST",
              "header": [],
              "body": {
                "mode": "raw",
                "raw": "{\r\n  \"productId\": 10,\r\n  \"quantity\": 0\r\n}",
                "options": {
                  "raw": {
                    "language": "json"
                  }
                }
              },
              "url": {
                "raw": "{{url_shop}}/cart",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "cart"
                ]
              }
            },
            "response": [],
            "uid": "44723816-b309454d-3081-4f5e-b018-89038a2dda80"
          },
          {
            "name": "Показать содержимое корзины",
            "event": [
              {
                "listen": "prerequest",
                "script": {
                  "id": "288c7e8b-a8d5-4646-a4f5-6f094634ae6d",
                  "exec": [
                    ""
                  ],
                  "type": "text/javascript",
                  "packages": {

                  }
                }
              },
              {
                "listen": "test",
                "script": {
                  "id": "79c32a84-6c80-42dd-850e-716a3a9f0bec",
                  "exec": [
                    "const response = pm.response.json();\r",
                    "\r",
                    "const cartitemid = response[0].cart_item_id;\r",
                    "\r",
                    "pm.collectionVariables.set(\"cartitemid\", cartitemid);\r",
                    "\r",
                    "console.log(\"Save cartitemid:\", cartitemid);\r",
                    ""
                  ],
                  "type": "text/javascript",
                  "packages": {

                  }
                }
              }
            ],
            "id": "c6ef1b02-a667-43b7-a9c0-c9948b7091a2",
            "protocolProfileBehavior": {
              "disableBodyPruning": true,
              "followAuthorizationHeader": false
            },
            "request": {
              "method": "GET",
              "header": [],
              "url": {
                "raw": "{{url_shop}}/getCart",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "getCart"
                ]
              }
            },
            "response": [],
            "uid": "44723816-c6ef1b02-a667-43b7-a9c0-c9948b7091a2"
          },
          {
            "name": "Обновление товара в корзине",
            "id": "83175729-c0cf-423c-bb15-c3ac03864c55",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "PATCH",
              "header": [],
              "body": {
                "mode": "raw",
                "raw": "{\r\n  \"quantity\": 0\r\n}",
                "options": {
                  "raw": {
                    "language": "json"
                  }
                }
              },
              "url": {
                "raw": "{{url_shop}}/cart/{{cartitemid}}",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "cart",
                  "{{cartitemid}}"
                ]
              }
            },
            "response": [],
            "uid": "44723816-83175729-c0cf-423c-bb15-c3ac03864c55"
          },
          {
            "name": "Удаление товара из корзины",
            "id": "27b55d29-7048-4b60-87d0-c0514fd2aa1b",
            "protocolProfileBehavior": {
              "disableBodyPruning": true
            },
            "request": {
              "method": "DELETE",
              "header": [],
              "body": {
                "mode": "raw",
                "raw": "{\r\n  \"productId\": 0,\r\n  \"quantity\": 0\r\n}",
                "options": {
                  "raw": {
                    "language": "json"
                  }
                }
              },
              "url": {
                "raw": "{{url_shop}}/cart/{{cartitemid}}",
                "host": [
                  "{{url_shop}}"
                ],
                "path": [
                  "cart",
                  "{{cartitemid}}"
                ]
              }
            },
            "response": [],
            "uid": "44723816-27b55d29-7048-4b60-87d0-c0514fd2aa1b"
          }
        ],
        "id": "cb9df86b-939b-47db-ae58-c3d34cea21d8",
        "uid": "44723816-cb9df86b-939b-47db-ae58-c3d34cea21d8"
      }
    ],
    "auth": {
      "type": "bearer",
      "bearer": [
        {
          "key": "token",
          "value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MTAyNiwiaWF0IjoxNzUzMjA5MTYxLCJleHAiOjE3NjE4NDkxNjF9.c8VmC-y6C998jvOHmw7IlDgwepVsCg8WdYgGpVgiDeY",
          "type": "string"
        }
      ]
    },
    "event": [
      {
        "listen": "prerequest",
        "script": {
          "id": "a02321c9-ae48-4a8c-9a6e-7c681ceb08a5",
          "type": "text/javascript",
          "packages": {

          },
          "exec": [
            ""
          ]
        }
      },
      {
        "listen": "test",
        "script": {
          "id": "a69a4506-0524-4bf7-ad1d-eeb55643be98",
          "type": "text/javascript",
          "packages": {

          },
          "exec": [
            ""
          ]
        }
      }
    ],
    "variable": [
      {
        "key": "url_shop",
        "value": "https://intern.demoshopping.ru",
        "type": "string"
      },
      {
        "key": "username",
        "value": "",
        "type": "string"
      },
      {
        "key": "password",
        "value": "",
        "type": "string"
      },
      {
        "key": "cartitemid",
        "value": ""
      },
      {
        "key": "productID",
        "value": ""
      }
    ]
  }
