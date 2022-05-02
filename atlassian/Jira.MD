# Install Atlassian Jira Software on Docker with Crack

## Create jira-software Directory

Create Directory `Jira-software`

copy [jira-compose.yml](https://github.com/beigi-reza/My-Wiki/blob/main/atlassian/jira-compose.yml) in `Jira-software` directory

copy [atlassian-agent.bak](https://github.com/beigi-reza/My-Wiki/blob/main/atlassian/crack/atlassian-agent.bak) in `Jira-software/crack` directory


```bash
mkdir -p jira-software/crack
cd jira-software

wget https://github.com/beigi-reza/My-Wiki/blob/main/atlassian/jira-compose.yml

cd crack 
wget https://github.com/beigi-reza/My-Wiki/blob/main/atlassian/crack/atlassian-agent.bak
```


## Run Jira(Compose File)

```bash
docker-compose -f jira-compose.yml up -d
```
> Use `http://<ip>:8080`


## Crack Jira

1. open `http://<ip>:8080` on browser
2. Edit Name & Address & click Next
2. When asked for license

### Get key From Agent

*Run `atlassian-agent.jar`** in **jira container*

**syntax**

>**java -jar atlassian-agent.jar -m `<your email>` -o `<your organization>` -p `<product to activate>` -s `<Server ID>` & Enter**



Run in Bash
```bash
docker exec -it jira-software java -jar /atlassian-agent.jar -m test@gmail.com -o test -p jira -s B0F2-VAOH-QRK0-E331
```

- NOTE1: Server ID is shown at License request step on JIRA Setup wizard
- NOTE2: Product codes & more parameters can be obtained by executing `java -jar atlassian-agent.jar -h`

Copy produced license to Jira License request field & Click **Next**

**Done :)**



Reference for Crack: 

[atlassian-agent](https://gitee.com/pengzhile/atlassian-agent)