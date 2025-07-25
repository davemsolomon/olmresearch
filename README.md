'''
## install docker and minikube using downloads from the internet via the browser

minikube start 

C:\Users\davem\Desktop\k8s-2025>minikube status
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured

### install OLM into minikube
### https://operator-framework.github.io/olm-book/docs/install-olm.html
kubectl create -f https://raw.githubusercontent.com/operator-framework/operator-lifecycle-manager/master/deploy/upstream/quickstart/crds.yaml
kubectl create -f https://raw.githubusercontent.com/operator-framework/operator-lifecycle-manager/master/deploy/upstream/quickstart/olm.yaml

### catalogsource.yml
apiVersion: operators.coreos.com/v1alpha1
kind: CatalogSource
metadata:
  name: operatorhubio-catalog
  namespace: olm
spec:
  sourceType: grpc
  image: quay.io/operatorhubio/catalog:latest
  displayName: Community Operators
  publisher: OperatorHub.io

## apply catalogsource.yml
C:\Users\davem\Desktop\k8s-2025>kubectl apply -f ./catalogsource.yml

### https://olm.operatorframework.io/docs/troubleshooting/catalogsource/
C:\Users\davem\Desktop\k8s-2025>kubectl get catsrc operatorhubio-catalog -n olm -o yaml
apiVersion: operators.coreos.com/v1alpha1
kind: CatalogSource
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"operators.coreos.com/v1alpha1","kind":"CatalogSource","metadata":{"annotations":{},"name":"operatorhubio-catalog","namespace":"olm"},"spec":{"displayName":"Community Operators","image":"quay.io/operatorhubio/catalog:latest","publisher":"OperatorHub.io","sourceType":"grpc"}}
  creationTimestamp: "2025-07-25T07:23:57Z"
  generation: 1
  name: operatorhubio-catalog
  namespace: olm
  resourceVersion: "1505"
  uid: 3468acd6-adb5-4352-83d2-c71e7bf67d2f
spec:
  displayName: Community Operators
  image: quay.io/operatorhubio/catalog:latest
  publisher: OperatorHub.io
  sourceType: grpc
  updateStrategy:
    registryPoll:
      interval: 60m
status:
  connectionState:
    address: operatorhubio-catalog.olm.svc:50051
    lastConnect: "2025-07-25T07:26:27Z"
    lastObservedState: READY
  registryService:
    createdAt: "2025-07-25T07:24:30Z"
    port: "50051"
    protocol: grpc
    serviceName: operatorhubio-catalog
    serviceNamespace: olm

### https://olm.operatorframework.io/docs/troubleshooting/catalogsource/
C:\Users\davem\Desktop\k8s-2025>kubectl -n olm get packagemanifests
NAME                                       CATALOG               AGE
apicurio-api-controller                    Community Operators   3m16s
ack-route53-controller                     Community Operators   3m16s
krateo-installer                           Community Operators   3m16s
datadog-operator                           Community Operators   3m16s
hedvig-operator                            Community Operators   3m16s
ack-wafv2-controller                       Community Operators   3m16s
ecr-secret-operator                        Community Operators   3m16s
kernel-module-management                   Community Operators   3m16s
openebs                                    Community Operators   3m16s
t8c                                        Community Operators   3m16s
skydive-operator                           Community Operators   3m16s
ack-cloudwatch-controller                  Community Operators   3m16s
pubsubplus-eventbroker-operator            Community Operators   3m16s
kaap                                       Community Operators   3m16s
litmuschaos                                Community Operators   3m16s
atlasmap-operator                          Community Operators   3m16s
kepler-operator                            Community Operators   3m16s
kubeturbo                                  Community Operators   3m16s
wandb-operator                             Community Operators   3m16s
ack-networkfirewall-controller             Community Operators   3m16s
ack-organizations-controller               Community Operators   3m16s
hpa-operator                               Community Operators   3m16s
kubefed-operator                           Community Operators   3m16s
rabbitmq-cluster-operator                  Community Operators   3m16s
ack-cloudwatchlogs-controller              Community Operators   3m16s
ack-sfn-controller                         Community Operators   3m16s
wavefront                                  Community Operators   3m16s
edp-keycloak-operator                      Community Operators   3m16s
ack-route53resolver-controller             Community Operators   3m16s
istio                                      Community Operators   3m16s
gingersnap                                 Community Operators   3m16s
trident-operator                           Community Operators   3m16s
multicluster-operators-subscription        Community Operators   3m16s
nsm-operator-registry                      Community Operators   3m16s
grafana-operator                           Community Operators   3m16s
infisical-operator                         Community Operators   3m16s
virt-gateway-operator                      Community Operators   3m16s
steerd-presto-operator                     Community Operators   3m16s
aiven-operator                             Community Operators   3m16s
apch-operator                              Community Operators   3m16s
awss3-operator-registry                    Community Operators   3m16s
dapr-kubernetes-operator                   Community Operators   3m16s
postgresql-operator                        Community Operators   3m16s
ack-s3-controller                          Community Operators   3m16s
ack-dynamodb-controller                    Community Operators   3m16s
xrootd-operator                            Community Operators   3m16s
victoriametrics-operator                   Community Operators   3m16s
trivy-operator                             Community Operators   3m16s
ack-kinesis-controller                     Community Operators   3m16s
service-binding-operator                   Community Operators   3m16s
ack-sns-controller                         Community Operators   3m16s
synapse-operator                           Community Operators   3m16s
trustify-operator                          Community Operators   3m16s
ack-elasticache-controller                 Community Operators   3m16s
accuknox-operator                          Community Operators   3m16s
datatrucker-operator                       Community Operators   3m16s
lbconfig-operator                          Community Operators   3m16s
cryostat-operator                          Community Operators   3m16s
ibmcloud-iam-operator                      Community Operators   3m16s
clever-operator                            Community Operators   3m16s
portworx                                   Community Operators   3m16s
redis-operator                             Community Operators   3m16s
kube-green                                 Community Operators   3m16s
openshift-qiskit-operator                  Community Operators   3m16s
machine-deletion-operator                  Community Operators   3m16s
jhipster-online-operator                   Community Operators   3m16s
fossul-operator                            Community Operators   3m16s
mongodb-enterprise                         Community Operators   3m16s
external-secrets-operator                  Community Operators   3m16s
skupper-operator                           Community Operators   3m16s
redis-enterprise                           Community Operators   3m16s
ripsaw                                     Community Operators   3m16s
percona-xtradb-cluster-operator            Community Operators   3m16s
neuvector-operator                         Community Operators   3m16s
ack-sagemaker-controller                   Community Operators   3m16s
enc-key-sync                               Community Operators   3m16s
sematext                                   Community Operators   3m16s
jaeger                                     Community Operators   3m16s
hive-operator                              Community Operators   3m16s
postgresql                                 Community Operators   3m16s
konveyor-operator                          Community Operators   3m16s
tf-operator                                Community Operators   3m16s
kubernetes-nmstate-operator                Community Operators   3m16s
ack-pipes-controller                       Community Operators   3m16s
nexus-operator-m88i                        Community Operators   3m16s
argocd-operator                            Community Operators   3m16s
aws-auth-operator                          Community Operators   3m16s
patterns-operator                          Community Operators   3m16s
ack-ram-controller                         Community Operators   3m16s
k8gb                                       Community Operators   3m16s
aerospike-kubernetes-operator              Community Operators   3m16s
ack-iam-controller                         Community Operators   3m16s
topolvm-operator                           Community Operators   3m16s
apicurio-registry                          Community Operators   3m16s
mysql                                      Community Operators   3m16s
verticadb-operator                         Community Operators   3m16s
routernetes-operator                       Community Operators   3m16s
composable-operator                        Community Operators   3m16s
hyperfoil-bundle                           Community Operators   3m16s
nuxeo-operator                             Community Operators   3m16s
kubernetes-imagepuller-operator            Community Operators   3m16s
ceph-s3-operator                           Community Operators   3m16s
zoperator                                  Community Operators   3m16s
lib-bucket-provisioner                     Community Operators   3m16s
ack-ses-controller                         Community Operators   3m16s
dnext-operator                             Community Operators   3m16s
flux                                       Community Operators   3m16s
percona-server-mongodb-operator            Community Operators   3m16s
opentelemetry-operator                     Community Operators   3m16s
microcks                                   Community Operators   3m16s
pystol                                     Community Operators   3m16s
sosivio                                    Community Operators   3m16s
self-node-remediation                      Community Operators   3m16s
tempo-operator                             Community Operators   3m16s
cass-operator-community                    Community Operators   3m16s
strimzi-kafka-operator                     Community Operators   3m16s
ublhub-operator                            Community Operators   3m16s
falco                                      Community Operators   3m16s
vault                                      Community Operators   3m16s
mercury-operator                           Community Operators   3m16s
cte-k8s-operator                           Community Operators   3m16s
apicurio-registry-3                        Community Operators   3m16s
noobaa-operator                            Community Operators   3m16s
integrity-shield-operator                  Community Operators   3m16s
marin3r                                    Community Operators   3m16s
parodos-operator                           Community Operators   3m16s
ack-s3control-controller                   Community Operators   3m16s
ack-cognitoidentityprovider-controller     Community Operators   3m16s
kuadrant-operator                          Community Operators   3m16s
camel-k                                    Community Operators   3m16s
dns-operator                               Community Operators   3m16s
ack-cloudtrail-controller                  Community Operators   3m16s
layer7-operator                            Community Operators   3m16s
druid-operator                             Community Operators   3m16s
nfs-operator                               Community Operators   3m16s
meshery-operator                           Community Operators   3m16s
myvirtualdirectory                         Community Operators   3m16s
yugabyte-operator                          Community Operators   3m16s
portworx-essentials                        Community Operators   3m16s
node-maintenance-operator                  Community Operators   3m16s
node-healthcheck-operator                  Community Operators   3m16s
multi-nic-cni-operator                     Community Operators   3m16s
ack-opensearchserverless-controller        Community Operators   3m16s
ack-apigatewayv2-controller                Community Operators   3m16s
ack-kafka-controller                       Community Operators   3m16s
kube-loxilb-operator                       Community Operators   3m16s
ham-deploy                                 Community Operators   3m16s
ack-lambda-controller                      Community Operators   3m16s
pcc-operator                               Community Operators   3m16s
universal-crossplane                       Community Operators   3m16s
sonar-operator                             Community Operators   3m16s
ack-mq-controller                          Community Operators   3m16s
qserv-operator                             Community Operators   3m16s
event-streams-topic                        Community Operators   3m16s
ack-efs-controller                         Community Operators   3m16s
apicast-community-operator                 Community Operators   3m16s
ack-apigateway-controller                  Community Operators   3m16s
pmem-csi-operator                          Community Operators   3m16s
radanalytics-spark                         Community Operators   3m16s
ack-emrcontainers-controller               Community Operators   3m16s
elastic-phenix-operator                    Community Operators   3m16s
carbonetes-operator                        Community Operators   3m16s
airflow-helm-operator                      Community Operators   3m16s
spinnaker-operator                         Community Operators   3m16s
keycloak-operator                          Community Operators   3m16s
mcad-operator                              Community Operators   3m16s
elastic-cloud-eck                          Community Operators   3m16s
anchore-engine                             Community Operators   3m16s
percona-postgresql-operator                Community Operators   3m16s
azure-service-operator                     Community Operators   3m16s
kubeflow                                   Community Operators   3m16s
loki-operator                              Community Operators   3m16s
nacos-operator                             Community Operators   3m16s
shipwright-operator                        Community Operators   3m16s
hpe-ezmeral-csi-operator                   Community Operators   3m16s
ack-sqs-controller                         Community Operators   3m16s
registry-operator                          Community Operators   3m16s
openshift-node-upgrade-mutex-operator      Community Operators   3m16s
rook-edgefs                                Community Operators   3m16s
varnish-operator                           Community Operators   3m16s
metering-upstream                          Community Operators   3m16s
windup-operator                            Community Operators   3m16s
debezium-operator                          Community Operators   3m16s
integration-operator                       Community Operators   3m16s
gitlab-operator-kubernetes                 Community Operators   3m16s
ack-acmpca-controller                      Community Operators   3m16s
minio-operator                             Community Operators   3m16s
tektoncd-operator                          Community Operators   3m16s
seldon-operator                            Community Operators   3m16s
siddhi-operator                            Community Operators   3m16s
searchpe-operator                          Community Operators   3m16s
datasance-pot-operator                     Community Operators   3m16s
deployment-validation-operator             Community Operators   3m16s
kubero-operator                            Community Operators   3m16s
monocle-operator                           Community Operators   3m16s
sap-btp-operator                           Community Operators   3m16s
ack-athena-controller                      Community Operators   3m16s
wildfly                                    Community Operators   3m16s
ack-cloudfront-controller                  Community Operators   3m16s
nfs-provisioner-operator                   Community Operators   3m16s
traefikee-operator                         Community Operators   3m16s
ack-eks-controller                         Community Operators   3m16s
ibm-application-gateway-operator           Community Operators   3m16s
camel-karavan-operator                     Community Operators   3m16s
beegfs-csi-driver-operator                 Community Operators   3m16s
quay-api-operator                          Community Operators   3m16s
nfd-operator                               Community Operators   3m16s
netobserv-operator                         Community Operators   3m16s
infinispan                                 Community Operators   3m16s
cluster-manager                            Community Operators   3m16s
temporal-operator                          Community Operators   3m16s
storageos                                  Community Operators   3m16s
ack-applicationautoscaling-controller      Community Operators   3m16s
clickhouse                                 Community Operators   3m16s
aqua                                       Community Operators   3m16s
ack-rds-controller                         Community Operators   3m16s
akka-cluster-operator                      Community Operators   3m16s
kom-operator                               Community Operators   3m16s
ack-memorydb-controller                    Community Operators   3m16s
otc-rds-operator                           Community Operators   3m16s
rocketmq-operator                          Community Operators   3m16s
splunk                                     Community Operators   3m16s
postgresql-operator-dev4devs-com           Community Operators   3m16s
bookkeeper-operator                        Community Operators   3m16s
iot-simulator                              Community Operators   3m16s
parseable-operator                         Community Operators   3m16s
ack-prometheusservice-controller           Community Operators   3m16s
tidb-operator                              Community Operators   3m16s
community-trivy-operator                   Community Operators   3m16s
ibm-spectrum-scale-csi-operator            Community Operators   3m16s
enmasse                                    Community Operators   3m16s
spark-gcp                                  Community Operators   3m16s
zookeeper-operator                         Community Operators   3m16s
eginnovations-operator                     Community Operators   3m16s
community-kubevirt-hyperconverged          Community Operators   3m16s
ack-codeartifact-controller                Community Operators   3m16s
instaslice-operator                        Community Operators   3m16s
cluster-impairment-operator                Community Operators   3m16s
cc-operator                                Community Operators   3m16s
sonataflow-operator                        Community Operators   3m16s
rabbitmq-messaging-topology-operator       Community Operators   3m16s
prometheus-exporter-operator               Community Operators   3m16s
keydb-operator                             Community Operators   3m16s
galaxy-operator                            Community Operators   3m16s
kong-gateway-operator                      Community Operators   3m16s
ibm-quantum-operator                       Community Operators   3m16s
ack-ecr-controller                         Community Operators   3m16s
function-mesh                              Community Operators   3m16s
prometheus                                 Community Operators   3m16s
flagsmith                                  Community Operators   3m16s
pinot-operator                             Community Operators   3m16s
hazelcast-platform-operator                Community Operators   3m16s
esindex-operator                           Community Operators   3m16s
leaksignal-operator                        Community Operators   3m16s
ack-kms-controller                         Community Operators   3m16s
gitlab-runner-operator                     Community Operators   3m16s
kaoto-operator                             Community Operators   3m16s
apimatic-kubernetes-operator               Community Operators   3m16s
pulsar-operator                            Community Operators   3m16s
cloudnative-pg                             Community Operators   3m16s
tf-controller                              Community Operators   3m16s
oci-ccm-operator                           Community Operators   3m16s
pulsar-resources-operator                  Community Operators   3m16s
cockroachdb                                Community Operators   3m16s
project-quay                               Community Operators   3m16s
vault-helm                                 Community Operators   3m16s
cassandra-operator                         Community Operators   3m16s
mongodb-operator                           Community Operators   3m16s
kernel-module-management-hub               Community Operators   3m16s
planetscale                                Community Operators   3m16s
jenkins-operator                           Community Operators   3m16s
postgres-operator-krestomatio              Community Operators   3m16s
federatorai                                Community Operators   3m16s
pixie-operator                             Community Operators   3m16s
oracle-database-operator                   Community Operators   3m16s
sailoperator                               Community Operators   3m16s
chaosblade-operator                        Community Operators   3m16s
bpfman-operator                            Community Operators   3m16s
metallb-operator                           Community Operators   3m16s
couchbase-enterprise                       Community Operators   3m16s
dell-csm-operator                          Community Operators   3m16s
ack-ssm-controller                         Community Operators   3m16s
nri-plugins-operator                       Community Operators   3m16s
ack-opensearchservice-controller           Community Operators   3m16s
banzaicloud-kafka-operator                 Community Operators   3m16s
ovms-operator                              Community Operators   3m16s
ack-eventbridge-controller                 Community Operators   3m16s
app-director-operator                      Community Operators   3m16s
rsct-operator                              Community Operators   3m16s
halkyon                                    Community Operators   3m16s
susql-operator                             Community Operators   3m16s
snapscheduler                              Community Operators   3m16s
kogito-operator                            Community Operators   3m16s
api-operator                               Community Operators   3m16s
klusterlet                                 Community Operators   3m16s
lightbend-console-operator                 Community Operators   3m16s
ibm-security-verify-directory-operator     Community Operators   3m16s
kube-arangodb                              Community Operators   3m16s
ipfs-operator                              Community Operators   3m16s
flux-operator                              Community Operators   3m16s
mariadb-operator-app                       Community Operators   3m16s
application-services-metering-operator     Community Operators   3m16s
hpe-csi-operator                           Community Operators   3m16s
kong                                       Community Operators   3m16s
ack-elbv2-controller                       Community Operators   3m16s
cluster-aas-operator                       Community Operators   3m16s
project-quay-container-security-operator   Community Operators   3m16s
github-arc-operator                        Community Operators   3m16s
sigstore-helm-operator                     Community Operators   3m16s
flink-kubernetes-operator                  Community Operators   3m16s
kubemod                                    Community Operators   3m16s
tagger                                     Community Operators   3m16s
sap-hana-express-operator                  Community Operators   3m16s
keycloak-permissions-operator              Community Operators   3m16s
mondoo-operator                            Community Operators   3m16s
pulp-operator                              Community Operators   3m16s
ibm-block-csi-operator-community           Community Operators   3m16s
intel-ethernet-operator                    Community Operators   3m16s
mariadb-operator                           Community Operators   3m16s
submariner                                 Community Operators   3m16s
ember-csi-operator                         Community Operators   3m16s
ndb-operator                               Community Operators   3m16s
robin-operator                             Community Operators   3m16s
hawkbit-operator                           Community Operators   3m16s
log2rbac                                   Community Operators   3m16s
ack-bedrockagent-controller                Community Operators   3m16s
trustee-operator                           Community Operators   3m16s
moodle-operator                            Community Operators   3m16s
ack-recyclebin-controller                  Community Operators   3m16s
yaks                                       Community Operators   3m16s
ack-keyspaces-controller                   Community Operators   3m16s
ack-ecrpublic-controller                   Community Operators   3m16s
authorino-operator                         Community Operators   3m16s
mongodb-atlas-kubernetes                   Community Operators   3m16s
rabbitmq-single-active-consumer-operator   Community Operators   3m16s
ack-ec2-controller                         Community Operators   3m16s
limitador-operator                         Community Operators   3m16s
ack-secretsmanager-controller              Community Operators   3m16s
perses-operator                            Community Operators   3m16s
kyverno-operator                           Community Operators   3m16s
argocd-operator-helm                       Community Operators   3m16s
alloydb-omni-operator                      Community Operators   3m16s
kubestone                                  Community Operators   3m16s
etcd                                       Community Operators   3m16s
dynatrace-operator                         Community Operators   3m16s
keda                                       Community Operators   3m16s
istio-workspace-operator                   Community Operators   3m16s
ibm-security-verify-access-operator        Community Operators   3m16s
wso2am-operator                            Community Operators   3m16s
move2kube-operator                         Community Operators   3m16s
ack-acm-controller                         Community Operators   3m16s
ack-documentdb-controller                  Community Operators   3m16s
instana-agent-operator                     Community Operators   3m16s
api-testing-operator                       Community Operators   3m16s
kiali                                      Community Operators   3m16s
appdynamics-operator                       Community Operators   3m16s
intel-device-plugins-operator              Community Operators   3m16s
telegraf-operator                          Community Operators   3m16s
ditto-operator                             Community Operators   3m16s
simple-authenticator                       Community Operators   3m16s
logging-operator                           Community Operators   3m16s
stackgres                                  Community Operators   3m16s
knative-operator                           Community Operators   3m16s
rook-ceph                                  Community Operators   3m16s
mongodb-kubernetes                         Community Operators   3m16s
sn-operator                                Community Operators   3m16s
prometurbo                                 Community Operators   3m16s
credstash-operator                         Community Operators   3m16s
alvearie-imaging-ingestion                 Community Operators   3m16s
silicom-sts-operator                       Community Operators   3m16s
ks-releaser-operator                       Community Operators   3m16s
kubensync                                  Community Operators   3m16s
joget-tomcat-operator                      Community Operators   3m16s
kubemq-operator                            Community Operators   3m16s
ack-ecs-controller                         Community Operators   3m16s
ext-postgres-operator                      Community Operators   3m16s
ibmcloud-operator                          Community Operators   3m16s
horreum-operator                           Community Operators   3m16s
security-profiles-operator                 Community Operators   3m16s
starboard-operator                         Community Operators   3m16s
hawtio-operator                            Community Operators   3m16s
appranix                                   Community Operators   3m16s
kubearmor-operator                         Community Operators   3m16s
customized-user-remediation                Community Operators   3m16s
postgres-operator                          Community Operators   3m16s
eventing-kogito                            Community Operators   3m16s
lms-moodle-operator                        Community Operators   3m16s
ndmspc-operator                            Community Operators   3m16s
cos-bucket-operator                        Community Operators   3m16s
nexus-operator                             Community Operators   3m16s
fence-agents-remediation                   Community Operators   3m16s
cert-manager                               Community Operators   3m16s
