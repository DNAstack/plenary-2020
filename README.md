# plenary-2020


## Getting running in 4 commands:


```
docker pull postgres:latest
docker run -d --rm --network="host" --name dnastack-ga4gh-search-db -e POSTGRES_USER=ga4ghsearchadapterpresto -e POSTGRES_PASSWORD=ga4ghsearchadapterpresto postgres
docker pull gcr.io/dnastack-container-store/search-presto:prod-us
docker run --rm --name dnastack-ga4gh-search -p 8089:8089 -e PRESTO_DATASOURCE_URL=https://presto-public.prod.dnastack.com -e SPRING_PROFILES_ACTIVE=no-auth search
```


## Set up your local Pres