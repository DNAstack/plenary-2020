# GA4GH Search Plenary 2020 Demo DIY Instructions

## Intro:

Follow these steps to get a reference implementation of GA4GH Search up and running in 30 seconds.


## Getting running in 4 commands:

```
docker pull postgres:latest
docker run -d --rm --network="host" --name dnastack-ga4gh-search-db -e POSTGRES_USER=ga4ghsearchadapterpresto -e POSTGRES_PASSWORD=ga4ghsearchadapterpresto postgres
docker pull dnastack/ga4gh-search-adapter-presto:latest
docker run --rm --name dnastack-ga4gh-search -p 8089:8089 -e PRESTO_DATASOURCE_URL=https://presto-public.prod.dnastack.com -e SPRING_PROFILES_ACTIVE=no-auth dnastack/ga4gh-search-adapter-presto:latest
```

These commands will:
1. Download Postgres
2. Start it up locally
3. Download the Search implementation
4. Start it up locally, pointing to an instance of Presto (i.e. a data source) hosted by DNAstack. 


## A Sample Query

POST this as a JSON body to `http://localhost:8089/search`

```
{
	"query": "SELECT * FROM search_postgres_pgpc.ontology.axiom"
}
```

## Check out the documentation and source code:

https://github.com/dnastack/ga4gh-search-adapter-presto

Check out the repo for:
- Additional setup configurations
- Providing custom data sources