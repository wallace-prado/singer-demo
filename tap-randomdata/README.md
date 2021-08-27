# Singer Demo

## Intro

This Singer Tap implements a simple way to generate random data, using https://random-data-api.com/ as source.

## Install

pip install tap-randomdata

## Available Streams

This Tap supports the Streams listed below:

- Company
- Restaurant
- Address
- Vehicle
- Food

Please, check https://random-data-api.com/documentation for more information.

## Config

To execute the Tap in Sync Mode you have to provide a config.json file.

There is only one required key: record_count. It must be a integer and represents the number of record to be generated.

Please check [sample_file](tap-randomdata/sample_config.json) for an example.

## Run Tap

e.g.

    tap-randomdata -c sample_config.json | target-<your-choice>

## How to create new Streams

1. Check [Random Data](https://random-data-api.com/documentation) to see supported endpoints and choose one (e.g. food).
2. Click on the endpoint to get a json example. Use this example to create a json schema. Use https://www.jsonschema.net/home for that.
3. With the generated schema, create a new schema file \<stream>.json (e.g. food.json) in [schemas](tap_randomdata/schemas) directory. It will support Tap Dicover mode.
4. In [__init__.py](tap_randomdata/__init__.py) add the new stream in the dict RANDOMDATA_PATH. The key must be the name of the stream (e.g. food) and the value is the path to the endpoint (e.g. /food/random_food)

That's it!