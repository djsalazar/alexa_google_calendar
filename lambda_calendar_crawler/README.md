# lambda_calendar_crawler
Get events information from google calendar.

## Overview

This lambda function get google calendar data(ics file).
It store event information in DynamoDB.
If the event is not changed(begin date, start hour, summary), it do nothing.

## Installation

```
cd lambda_calendar_crawler
pip install -r requirements.txt -t $(pwd)
```

compress all files in to zip.
```
zip -r func.zip .
```

## Create Amazon DynamoDB table.

  ``` shell
  # create table
  aws dynamodb create-table --table-name calendar_event \
  --attribute-definitions AttributeName=uid,AttributeType=S AttributeName=begin_date,AttributeType=S \
  --key-schema AttributeName=uid,KeyType=HASH AttributeName=begin_date,KeyType=RANGE \
  --provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1
```
