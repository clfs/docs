# GCP

## Spot instance

Create a spot instance that self-deletes after 30 minutes:

```plaintext
gcloud compute instances create my-cool-instance \
    --zone us-central1-a \
    --machine-type n4a-standard-2 \
    --image-project ubuntu-os-cloud \
    --image-family ubuntu-minimal-2510-arm64 \
    --max-run-duration 30m \
    --provisioning-model SPOT \
    --instance-termination-action DELETE
```

Connect, stop, or delete:

```plaintext
gcloud compute ssh my-cool-instance
gcloud compute instances stop my-cool-instance
gcloud compute instances delete my-cool-instance
```
