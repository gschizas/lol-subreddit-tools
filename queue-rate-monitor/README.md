# Queue rate monitor

Monitors submission rates of a queue (ex. new), and sends a message to Slack for high activity.

*Note:* Still being developed.

## Requirements

* Python 3+ (tested on 3.5)

Additional Python requirements are outlined in `requirements.txt`.

## Usage

    python queue_rate.py

Should be set up with a scheduler (ex. cron) to run regularly.

## Configuration

The following settings are available at the top of `queue_rate.py`.

|Name|Type|Description|Example|
:--|:-:|:--|:--
subreddit|string|Subreddit being monitored (without `/r/`).|`"mysubreddit"`
queue|string|Queue name being monitored. Available queues: `new`, `rising`|`"new"`, `"rising"`
rate_threshold|float/int|Threshold of posts per second. Expressions make it easy to read.|`1/2`
|||
slack_webhook|string|Slack web hook integration URL|`"https://hooks.slack.com/services/we3srhas/34rygway/f02q9uaw98usdijfhaosidjad"`
slack_channels|list(string)|List of Slack channels to send messages. If `None` sends to the default integration channel.|`["general", "warnings"]`
slack_message|string|Message to send. Formatted with `{queue}`, `{posts}`, and `{time}`.|`"{queue} has become super active: {posts} posts made in {time} seconds"`
