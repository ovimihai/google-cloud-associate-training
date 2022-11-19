
## Create a persistent state in Cloud Shell

1. List available regions `gcloud compute regions list`
2. Create a variable with your region `export INFRACLASS_REGION=us-west4`
3. Check value `echo $INFRACLASS_REGION`

*Create a persisten environment*
```bash
export INFRACLASS_REGION=us-west4
export INFRACLASS_PROJECT_ID=qwiklabs-gcp-02-8ecf6225a660
```

```bash
mkdir -p infraclass
touch infraclass/config
echo INFRACLASS_REGION=$INFRACLASS_REGION >> ~/infraclass/config
echo INFRACLASS_PROJECT_ID=$INFRACLASS_PROJECT_ID >> ~/infraclass/config

echo "source infraclass/config" >> ~/.profile
```

*Use environment*

```bash
source infraclass/config
echo $INFRACLASS_PROJECT_ID
```
