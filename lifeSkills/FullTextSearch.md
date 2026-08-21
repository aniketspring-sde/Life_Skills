# Investigation of Elasticsearch, Solr, and Lucene for Full-Text Search

## Introduction

Modern applications store a huge amount of text data, such as product
details, emails, documents, blogs, and user comments. As the amount of
data grows, searching it using a traditional SQL database becomes
slower. Queries like `LIKE '%keyword%'` have to scan many records, which
affects performance. To solve this problem, developers use dedicated
full-text search engines such as **Apache Lucene**, **Elasticsearch**,
and **Apache Solr**.

## What is Full-Text Search?

Full-text search is a way of searching the complete content of a
document instead of matching only exact values. It can quickly find
related words and phrases, rank the most relevant results, and even
handle small spelling mistakes. This provides faster and more accurate
search results than a normal SQL query.

## Why Traditional Databases Are Slow

``` sql
SELECT * FROM books
WHERE title LIKE '%Harry%';
```

This query checks many rows before finding matching records. When the
database contains millions of records, the search becomes slow and uses
more CPU and memory. Traditional databases are designed for storing
data, not for performing large-scale text searches.

## What is an Inverted Index?

An **Inverted Index** stores each word along with the documents that
contain it.

  Word     Documents
  -------- -----------
  Java     1, 2
  Python   3
  Easy     1, 3

When someone searches for **Java**, the search engine immediately knows
that it appears in Documents 1 and 2.

## Apache Lucene

Apache Lucene is an open-source Java library used to build search
features. It provides very fast indexing and searching, but it is not a
database or a server.

**Advantages**

-   Very fast
-   Lightweight
-   Highly customizable

**Disadvantages**

-   Java only
-   No REST API
-   No built-in clustering

## Elasticsearch

Elasticsearch is a search engine built on top of Lucene. It provides
distributed search, REST APIs, automatic scaling, and near real-time
indexing.

**Advantages**

-   Fast and scalable
-   Easy to integrate
-   High availability

**Disadvantages**

-   Uses more memory
-   Requires server management

## Apache Solr

Apache Solr is another search platform built on Lucene. It provides
faceted search, advanced caching, filtering, and distributed search.

**Advantages**

-   Enterprise-ready
-   Excellent caching
-   Powerful search features

**Disadvantages**

-   More difficult to configure
-   Smaller community than Elasticsearch

## Comparison

| Feature | Lucene | Elasticsearch | Solr |
|---|---|---|---|
| **Type** | Java Search Library | Distributed Search Engine | Enterprise Search Platform |
| **REST API** | No | Yes | Yes |
| **Distributed Search** | No | Yes | Yes |
| **Built On** | — | Apache Lucene | Apache Lucene |
| **Best For** | Embedded search in Java applications | Large-scale distributed applications | Enterprise search applications |
| **Clustering** | No | Yes | Yes |
| **Ease of Use** | Requires programming | Easy through REST APIs | Easy through REST APIs |
| **Typical Use Cases** | Custom search functionality | Logs, analytics, product search, real-time search | Enterprise search, document indexing |

## Recommendation

For projects facing performance and scaling issues, **Elasticsearch** is
usually the best choice because it is fast, scalable, and easy to
integrate. **Solr** is a good option for enterprise applications, while
**Lucene** is suitable for embedded Java applications.

## Conclusion

Lucene, Elasticsearch, and Solr improve full-text search by using
indexing instead of scanning every database record. For most modern
applications, Elasticsearch is the preferred solution because it offers
high performance, scalability, and reliable search capabilities.


### References
- https://www.elastic.co/docs/reference/query-languages/query-dsl/full-text-queries
- https://lucene.apache.org/core/
- https://www.elastic.co/docs/reference/elasticsearch
- https://solr.apache.org/guide/solr/latest/index.html
