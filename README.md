# yss
`yss` is a tool that allows you to minimize Kubernetes yaml files by
generating them using a set of rules inspired by semantic markup
and Cascading Style Sheets. 

`yss` takes a YAML file and CSS file as input and outputs a larger 
amount of YAML. 
```
yss --yaml configmap.yaml --css classes.css
```

`yss` will inherit any rules defined on a particular YAML object. 

e.g. 

yss
```
metadata{
    namespace:my-namespace
}
```

The Kind field is treated the same as top level objects in the DOM. e.g
For example if you want all your CRDs to share a single config just do
something like the following.

yss
```
ClusterLogSink{
  spec:
  type: syslog
  host: example.com
  port: my-port
}
```
You can also apply classes by defining a `yss-class` anywhere in the YAML
definition.

yaml (excerpt)
```
spec:
  yss-class: tls-setting
  
```

yss (excerpt)
```
.tls-setting{
    enable-tls: true
}
```
