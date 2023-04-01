# Fly GitLab

Deploy GitLab to [Fly.io](https://fly.io)

## Setup

Create a new application and the necessary volumes:

```bash
fly apps create my-gitlab
fly volume create -a my-gitlab glab_data --size 10 # gb
fly volume create -a my-gitlab glab_logs --size 1 # gb
fly volume create -a my-gitlab glab_config --size 5 # gb
```

Update the `app` setting in `fly.toml` for your new app.
Then run the following:

```bash
flyctl deploy # deploy GitLab
fly machines update --memory 4096 --cpus 2 --select # scale compute resources
fly apps restart my-gitlab # ensure compute resources are used
```

