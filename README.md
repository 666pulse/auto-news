# Auto News
A personal news aggregator to pull information from multi-sources + LLM (ChatGPT) to help us reading efficiently with less noises, the sources includes: Tweets, RSS, YouTube, Article.

## Why need it?
In the world of this information explosion, we live with noise every day, it becomes even worse after the generative AI was born. Think about how much time we spent on pulling/searching/filtering content from different sources, how many times we put the article/paper or long video as a side tab, but never got a chance to look at, and how many efforts to organize the information we have read. We need a better way to get rid of the noises, and focus on reading the information efficient based on the interests, and stay on the track of the goals we defined.

placeholder: image for notion ui

## Architecture

placeholder: image for high-level architecture

## Hardware Requirement

| Component | Requirement |
| --------- | ----------- |
| Memory    | 6GB         |
| Disk      | 20GB+       |

# Installation
## Preparison
* Notion token (Required)
* Docker (Required)
* Twitter token (optional)

Copy `.env.template` to `build/.env`, and fill up the environment vars:
* `NOTION_TOKEN`
* `NOTION_DATABASE_ID_INDEX_INBOX`
* `NOTION_DATABASE_ID_INDEX_TOREAD`
* `OPENAI_API_KEY`
* [Optional] Vars with `TWITTER_` prefix

## Start Services
```bash
make build
make start
```

After 2 minutes, the services would be started, then enable DAGs:
```bash
make enable_dags
```

Now, the services are up and running, it will pull sources every hour.

## Set up Notion database views
Go to Notion, and create the database views for different source, e.g. Tweets, Article, Youtube, RSS, etc

## Control Panel
For troubleshooting, we can use the URLs below to access the services and check the logs and data

| Service | Responsibility  | Panel URL             |
| ---     | ---             | ---                   |
| Airflow | Orchestration   | http://localhost:8080 |
| Milvus  | Vector Database | http://localhost:9100 |
