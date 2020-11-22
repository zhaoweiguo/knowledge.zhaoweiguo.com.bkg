JSONPath Support [1]_
###########################

实例1
=====

json格式(如: k get po -o json)::

    {
      "kind": "List",
      "items":[
        {
          "kind":"None",
          "metadata":{"name":"127.0.0.1"},
          "status":{
            "capacity":{"cpu":"4"},
            "addresses":[{"type": "LegacyHostIP", "address":"127.0.0.1"}]
          }
        },
        {
          "kind":"None",
          "metadata":{"name":"127.0.0.2"},
          "status":{
            "capacity":{"cpu":"8"},
            "addresses":[
              {"type": "LegacyHostIP", "address":"127.0.0.2"},
              {"type": "another", "address":"127.0.0.3"}
            ]
          }
        }
      ],
      "users":[
        {
          "name": "myself",
          "user": {}
        },
        {
          "name": "e2e",
          "user": {"username": "admin", "password": "secret"}
        }
      ]
    }

函数说明::

    text:     kind is {.kind} 
    @:        {@} (the current object )
    . or []:  {.kind} or {[‘kind’]}
    ..:       {..name}
    *:        {.items[*].metadata.name} 
    [start:end :step]:    {.users[0].name}
    [,]:      {.items[*][‘metadata.name’, ‘status.capacity’]} 
    ?():      {.users[?(@.name==“e2e”)].user.password}  
    range, end:   {range .items[*]}[{.metadata.name}, {.status.capacity}] {end} 
    “:            {range .items[*]}{.metadata.name}{’\t’}{end}

实例::

    kubectl get pods -o json
    kubectl get pods -o=jsonpath='{@}'
    kubectl get pods -o=jsonpath='{.items[0]}'
    kubectl get pods -o=jsonpath='{.items[0].metadata.name}'
    kubectl get pods -o=jsonpath='{range .items[*]}{.metadata.name}{"\t"}{.status.startTime}{"\n"}{end}'

On Windows::

    C:\> kubectl get pods -o=jsonpath="{range .items[*]}{.metadata.name}{'\t'}{.status.startTime}{'\n'}{end}"
    C:\> kubectl get pods -o=jsonpath="{range .items[*]}{.metadata.name}{\"\t\"}{.status.startTime}{\"\n\"}{end}"

实例2
=====

input::

    $ kubectl  get svc first-deployment -o yaml
    apiVersion: v1
    kind: Service
    metadata:
      creationTimestamp: "2020-04-22T06:44:41Z"
      labels:
        app: first-deployment
      name: first-deployment
      namespace: default
      resourceVersion: "529"
      selfLink: /api/v1/namespaces/default/services/first-deployment
      uid: a25ff4b7-0ee9-4fdc-b134-6c66f9431bc1
    spec:
      clusterIP: 10.110.122.106
      externalTrafficPolicy: Cluster
      ports:
      - nodePort: 31012
        port: 80
        protocol: TCP
        targetPort: 80
      selector:
        app: first-deployment
      sessionAffinity: None
      type: NodePort
    status:
      loadBalancer: {}

使用::

    $ export PORT=$(kubectl get svc first-deployment \
      -o go-template='{{range.spec.ports}}{{if .nodePort}}{{.nodePort}}{{"\n"}}{{end}}{{end}}')









.. [1] https://kubernetes.io/docs/reference/kubectl/jsonpath/





