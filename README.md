# b0rkline

b0rk a Concourse - https://github.com/concourse/concourse/issues/1739#issuecomment-367032368

## Repro steps

```
vagrant init EngineerBetter/concourse-training-box --box-version 0.0.18
vagrant up
fly -t vm login -c http://localhost:8080
fly -t vm set-pipeline -p b0rk -c pipeline.yml
fly -t vm unpause-pipeline -p b0rk
fly -t vm trigger-job -j b0rk/b0rk
```

You should then start getting empty responses from the ATC, and if you `vagrant ssh` and poke around the Docker process for the ATC, you'll see the log messages from the linked GitHub issue.