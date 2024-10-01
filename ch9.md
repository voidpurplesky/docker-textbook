## 9.1
200
```
{
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "experimental": false,
  "insecure-registries": [
    "registry.local:5000"
  ],
  "matrics-addr": "127.0.0.1:9323",
  "experimental": true
}
```
$hostIP=$(Get-NetIPConfiguration | Where-Object {$._.IPv4DefaultGateway -ne $null}).IP4Address.IPAddress
hospIP=$(ip route get 1 | awk '{print $NF;exit}')
