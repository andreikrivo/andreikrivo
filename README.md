# raw copy of discord channel webhook URL
discord_webhook=""
url="${discord_webhook}/github"
# your target github org
org=""
# your target github org repo
repo=""

gh api /repos/"${org}"/"${repo}"/hooks \
  --input - <<< "{
  \"name\": \"web\",
  \"active\": true,
  \"events\": [
    \"*\"
  ],
  \"config\": {
    \"url\": \"${url}\",
    \"content_type\": \"json\"
  }
}"
