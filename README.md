# puzzly-keepalive

Free GitHub Actions pings that keep the Puzzly Render free-tier API awake.

- Target: `https://puzzly-api.onrender.com/api/healthz`
- Schedule: every 5 minutes (`*/5 * * * *`)
- Cost: $0 (public repo → unlimited Actions minutes for this workload)
- No secrets in workflows

## Why

Render free web services sleep after about 15 minutes idle. A ping every 5 minutes keeps `puzzly-api` warm so the first app request is not a cold start.

## Caveats

- GitHub scheduled workflows can run a few minutes late. Ten-minute spacing still usually stays under the 15-minute sleep window.
- GitHub may disable schedules after ~60 days with no repository activity. The `Monthly activity stamp` workflow commits a timestamp on the 1st of each month to prevent that.
- Free Render instances can still restart occasionally; that is separate from sleep.
- One free always-on web service uses about 720 of the 750 free instance hours/month.

## Manual run

Actions → **Keep puzzly-api awake** → Run workflow.
