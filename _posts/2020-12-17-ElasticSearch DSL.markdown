---
layout:     post
title:      "ElasticSearch DSL"
subtitle:   "busy"
date:       2020-12-17
author:     "Lydia"
header-img: "img/post-bg-design.jpg"
catalog: true
tags:
    - ElasticSearch
---

## 根据复杂条件分组聚合

```
http://xxx/_search

{
  "sort": [
    {
      "_score": {
        "order": "desc"
      }
    },
    {
      "create_time": {
        "order": "desc"
      }
    }
  ],
  "query": {
    "bool": {
      "filter": [
        {
          "term": {
            "task_id": "1"
          }
        },
        {
          "term": {
            "task_version": 1
          }
        },
        {
          "term": {
            "question_id": "1"
          }
        }
      ],
      "must": [
        {
          "term": {
            "answer_type": 1
          }
        },
        {
          "range": {
            "create_time": {
              "gte": 1607356800
            }
          }
        },
        {
          "range": {
            "create_time": {
              "lte": 1607443200
            }
          }
        }
      ]
    }
  },
  "aggs": {
    "answer": {
      "aggs": {
        "a_bucket": {
          "terms": {
            "field": "answer.rate"
          }
        }
      },
      "nested": {
        "path": "answer"
      }
    }
  }
}
```

## 根据条件去重统计

```
{
  "query": {
    "bool": {
      "filter": [
        {
          "term": {
            "plat_id": "1"
          }
        },
        {
          "term": {
            "task_id": "1"
          }
        },
        {
          "term": {
            "task_version": 1
          }
        }
      ],
      "must": [
        {
          "term": {
            "language": "zh_CN"
          }
        },
        {
          "range": {
            "create_time": {
              "gte": 1601481600000
            }
          }
        },
        {
          "range": {
            "create_time": {
              "lte": 1602777600000
            }
          }
        },
        {
          "nested": {
            "path": "custom_key",
            "query": {
              "bool": {
                "must_not": [
                  {
                    "terms": {
                      "custom_key.value": [
                        "a",
                        "b",
                        "c",
                        "d"
                      ]
                    }
                  }
                ],
                "must": [
                  {
                    "term": {
                      "custom_key.key": "type"
                    }
                  }
                ]
              }
            }
          }
        }
      ]
    }
  },
  "aggs": {
    "commit_distinct": {
      "cardinality": {
        "field": "submit_record_id"
      }
    }
  }
}
```



## 根据查询条件删除

```
http://xxx/_delete_by_query
```

---

未完待续