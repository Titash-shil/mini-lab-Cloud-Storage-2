# || [mini lab : Cloud Storage : 2](https://www.cloudskillsboost.google/games/5699/labs/36422) ||

## # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

---
## ⚠️ **Disclaimer:**
#### This script and guide are provided for educational purposes to help you understand the lab process. Please ensure you understand the steps before using any scripts. Before using the script, I encourage you to open and review it to understand each step.The goal is to help you learn how to complete the labs effectively while following Qwiklabs' terms of service and YouTube's community guidelines.
---

## Copy and run :

```
cat > lifecycle.json << EOF
{
    "rule": [
      {
        "action": {
          "storageClass": "NEARLINE",
          "type": "SetStorageClass"
        },
        "condition": {
          "daysSinceNoncurrentTime": 30,
          "matchesPrefix": [
            "/projects/active/"
          ]
        }
      },
      {
        "action": {
          "storageClass": "NEARLINE",
          "type": "SetStorageClass"
        },
        "condition": {
          "daysSinceNoncurrentTime": 90,
          "matchesPrefix": [
            "/archive/"
          ]
        }
      },
      {
        "action": {
          "storageClass": "COLDLINE",
          "type": "SetStorageClass"
        },
        "condition": {
          "daysSinceNoncurrentTime": 180,
          "matchesPrefix": [
            "/archive/"
          ]
        }
      },
      {
        "action": {
          "type": "Delete"
        },
        "condition": {
          "age": 7,
          "matchesPrefix": [
            "/processing/temp_logs/"
          ]
        }
      }
    ]
  }
EOF

export PROJECT_ID=$(gcloud config get-value project)

gsutil lifecycle set lifecycle.json gs://$PROJECT_ID-bucket
```
---

## Congratulations ..!!🎉  You completed the lab shortly..😃💯

## *Well done..!* 👏

## Thank you for visiting.... :) 🗯️

## [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN)

## Join to our community [Digital Dominators](https://chat.whatsapp.com/J0o1beFGCHfJ8ZHGKjcqkd)
