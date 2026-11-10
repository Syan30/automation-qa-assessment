# Hacker News Top Stories Automation

## Project Overview

An automated Hacker News monitoring workflow built using **n8n**, the Hacker News Firebase API, JavaScript, and Discord Webhooks.

The workflow automatically retrieves the top 5 Hacker News stories, fetches their details, sorts them by score, filters stories with more than 100 points, and sends formatted notifications to a Discord channel.

## Technologies Used

- **n8n:** Workflow automation and orchestration.
- **Hacker News Firebase API:** Fetching trending stories and their details.
- **JavaScript:** Data extraction, processing, sorting, and filtering.
- **Discord Webhooks:** Delivering automated notifications.

## Workflow Architecture

1. **Schedule Trigger:** Runs the workflow every hour.
2. **HTTP Request – Top Stories:** Retrieves story IDs from Hacker News.
3. **Code Node – Extract IDs:** Selects the first 5 story IDs.
4. **HTTP Request – Story Details:** Retrieves individual story information.
5. **Code Node – Process Stories:** Extracts titles, URLs, authors, scores, and publication timestamps, then sorts stories by score in descending order.
6. **Code Node – Filter and Format:** Filters stories scoring above 100 and formats them into a Discord message.
7. **HTTP Request – Discord:** Sends the formatted notification using a Discord webhook.

## API Endpoints

**Fetch Top Stories**

`GET https://hacker-news.firebaseio.com/v0/topstories.json`

**Fetch Individual Story**

`GET https://hacker-news.firebaseio.com/v0/item/{story_id}.json`

## Filtering Logic

Only stories with a score greater than 100 are included in Discord notifications.

Stories are sorted from highest to lowest score before filtering.

## Discord Notification

Each notification contains:

- Story title
- Score
- Author
- Original article URL

## Configuration

1. Create an n8n workflow.
2. Configure the Schedule Trigger to run every hour.
3. Add the Hacker News API HTTP Request nodes.
4. Configure the JavaScript Code nodes for extraction, processing, sorting, and filtering.
5. Create a Discord webhook and configure the final HTTP Request node.
6. Save and publish the workflow.

**Security:** Store webhook URLs securely. Never commit webhook tokens or other credentials to a public repository.

## Execution Results

The workflow was successfully tested and published.

The test execution retrieved 5 Hacker News stories, processed and sorted their details, filtered stories scoring above 100, and successfully delivered the resulting notification to Discord.

## Future Improvements

- Add error handling and retry mechanisms.
- Prevent duplicate story notifications.
- Store previously processed story IDs.
- Support multiple notification channels.
- Generate daily Hacker News summaries.

## Author

**Syed Anees**

Automation Workflow Project – Task 2s
