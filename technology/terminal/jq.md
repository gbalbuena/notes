# jq

## Key and values

### Extract keys

```bash
echo '{ "a": 1, "b": 2, "c": 3 }' | jq keys
[
  "a",
  "b",
  "c"
]
```



You can quickly create [filters](https://stedolan.github.io/jq/manual/#Basicfilters) to return a particular metric of the JSON file.

```bash
jq '. | select(.type=="Point" and .metric == "http_req_duration" and .data.tags.status >= "200")' myscript-output.json
```

And calculate an aggregated value of any metric.

```bash
// average
jq '. | select(.type=="Point" and .metric == "http_req_duration" and .data.tags.status >= "200") | .data.value' myscript-output.json | jq -s 'add/length'

// min
jq '. | select(.type=="Point" and .metric == "http_req_duration" and .data.tags.status >= "200") | .data.value' myscript-output.json | jq -s min

// max
jq '. | select(.type=="Point" and .metric == "http_req_duration" and .data.tags.status >= "200") | .data.value' myscript-output.json | jq -s max

```

