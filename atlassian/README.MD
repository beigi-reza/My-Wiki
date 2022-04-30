# Install Atlassian Jira Software on Docker with Crack

## Create jira-software Directory

Create Directory

```bash
mkdir -p jira-software/crack
cd jira-software

```

> rename `atlassian-agent.bak` to `atlassian-agent.jar` in crack folder

```bash
cd crack
mv atlassian-agent.bak atlassian-agent.jar
```

## Run compose File

```bash
docker-compose -f jira-compose.yml up -d
```
> Use `http://<ip>:8080`


## Crack Jira

### Run JIRA

1. Run Jira (Compse File)
2. open `http://<ip>:8080` on browser
3. When asked for license

### Get key From Agent

**Run `atlassian-agent.jar`** in jira container 

>java -jar atlassian-agent.jar -m `<your email>` -o `<your organization>` -p `<product to activate>` -s `<Server ID>` & Enter


```bash
docker exec -it jira-software bash
cd /

java -jar atlassian-agent.jar -m 1058@ronix.ir -o RONIX -p jira -s B0F2-VAOH-QRK0-E331
```
* NOTE1: Server ID is shown at License request step on JIRA Setup wizard
* NOTE2: Product codes & more parameters can be obtained by executing java -jar atlassian-agent.jar

**Copy produced license to Jira License request field**

Done :)