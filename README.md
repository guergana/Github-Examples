# Github-Examples
A repo containing GitHub for programmatic examples

+ Code from GitHub Actions Certification
https://www.youtube.com/watch?v=Tz7FsunBbfQ


## Cron Jobs
Page to generate cron expressions: https://crontab.guru/

## Dispatch workflows manually

For manual workflows to work we need to use `workflow_dispatch`.

```
gh workflow run greet.yml \
-f name=mona \
-f greeting=hello \
-F data=@myfile.txt
```

To pass in the parameters:

```
on:
    workflow_dispatch:
        inputs:
            name:
                description: 'Name of the person to greet'
                required: true
                type: string
            greeting:
                description: 'Type of greeting'
                required: true
                type: string
            data:
                description: 'Base64 encoded content of a file'
                required: true
                type: string

```

If we get a 403 we need to set GITHUB_TOKEN: https://github.com/settings/personal-access-tokens

then add the token here: `export GITHUB_TOKEN=<TOKEN>`

## Dependent jobs

Jobs usually run on parallel, if we want to run the sequentially, we need to use the `needs` keyword. See: `/github-actions/templates/dependent-jobs2.yml`