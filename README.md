# env-in-dvc

```
mamba install -c conda-forge dvc dvc-s3 hatch
```

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
