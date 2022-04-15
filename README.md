
## Standard Priority Order

 1. Deployment specific (e.g. client)
 2. Environment specific (e.g. dev, prd)
 3. Base (values.yaml)

 ```
helm install --dry-run --debug helm-test . -f ./stack-vars/dev/_global.yml,./stack-vars/dev/pocclient.yml

NAME: helm-test
LAST DEPLOYED: Fri Apr 15 12:19:27 2022
NAMESPACE: default
STATUS: pending-install
REVISION: 1
TEST SUITE: None
USER-SUPPLIED VALUES:
KEY2: global-dev-value
KEY3: owlbear-dev-value
KEY4: owlbear-dev-value

COMPUTED VALUES:
KEY1: base-value
KEY2: global-dev-value
KEY3: owlbear-dev-value
KEY4: owlbear-dev-value
```

## Swap Priority Around

 1. Environment specific (e.g. dev, prd)
 2. Deployment specific (e.g. owlbear, flextronics)
 3. Base (values.yaml)

Note, all of the deployment specific values will be overridden via the env specific

```
helm install --dry-run --debug helm-test . -f ./stack-vars/dev/pocclient.yml,./stack-vars/dev/_global.yml

NAME: helm-test
LAST DEPLOYED: Fri Apr 15 12:24:37 2022
NAMESPACE: default
STATUS: pending-install
REVISION: 1
TEST SUITE: None
USER-SUPPLIED VALUES:
KEY2: global-dev-value
KEY3: global-dev-value
KEY4: global-dev-value

COMPUTED VALUES:
KEY1: base-value
KEY2: global-dev-value
KEY3: global-dev-value
KEY4: global-dev-value
```