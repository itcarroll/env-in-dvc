# env-in-dvc

```
mamba install -c conda-forge dvc dvc-s3 hatch
```

Observations:
  1: github and gitlab actions have implemented caching for commonly used dependencies, somehow
  2: try the hatch-pip-compile lock to resolve locking for hatch

Questions:
  1: is this correct order for speed of environment creation (slow to fast)
    - solving environment
    - downloading
    - installing
  2: is dvc changing the exec bit or not?


## structures

1. set up in project
2. dvc import to /tmp (## IDK amounts to moving venv, fails?), or separate projects
```
~/path/to/project:
- .dvc
- .local
/tmp/local:
```

### home

1. git clone ...
2. dvc init
3. hatch config set dirs.env.virtual ".local/share/hatch"
4. hatch shell ## slow
5. dvc add .local/share/hatch ## really slow
6. dvc remote add --default origin $SCRATCH_BUCKET/env-in-dvc
7. dvc push
