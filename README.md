# GA4GH Search Plenary 2020 Demo DIY Instructions

## Intro:

Follow these steps to get up and running 


## Getting running in 4 commands:

```
docker pull postgres:latest
docker run -d --rm --network="host" --name dnastack-ga4gh-search-db -e POSTGRES_USER=ga4ghsearchadapterpresto -e POSTGRES_PASSWORD=ga4ghsearchadapterpresto postgres
docker pull dnastack/ga4gh-search-adapter-presto:latest
docker run --rm --name dnastack-ga4gh-search -p 8089:8089 -e PRESTO_DATASOURCE_URL=https://presto-public.prod.dnastack.com -e SPRING_PROFILES_ACTIVE=no-auth dnastack/ga4gh-search-adapter-presto:latest
```


## A Sample Query

POST this as a JSON body to `http://localhost:8089/search`

```
{
	"query": "SELECT * FROM search_postgres_pgpc.ontology.axiom"
}
```

## Check out the documentation and source code:

https://github.com/dnastack/ga4gh-search-adapter-presto