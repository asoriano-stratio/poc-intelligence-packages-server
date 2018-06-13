# Intelligence package server

## Pypi server
https://github.com/mosquito/pypi-server

## Apt package deb proxy
https://fabianlee.org/2018/02/08/ubuntu-a-centralized-apt-package-cache-using-squid-deb-proxy/

- Configuration file: /etc/squid-deb-proxy/squid-deb-proxy.conf
- Cache dir: /var/cache/squid-deb-proxy
- Service logs: /var/log/squid-deb-proxy (access.log cache.log store.log)


#### Client configuration

    echo "Acquire::http::Proxy \"http://X.X.X.X:8000\";" | sudo tee  /etc/apt/apt.conf.d/00proxy
    sudo apt-get update -q    


