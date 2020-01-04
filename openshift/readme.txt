
cd /tmp
wget https://github.com/minishift/minishift/releases/download/v1.34.0/minishift-1.34.0-linux-amd64.tgz
tar xzf minishift-1.34.0-linux-amd64.tgz
sudo cp minishift-1.34.0-linux-amd64/minishift /usr/local/bin
sudo chmod +x /usr/local/bin/minishift


minishift config set vm-driver virtualbox




./minishift start --vm-driver virtualbox --cpus 2 --memory 9000 --disk-size 100g

./minishift stop

./minishift delete

in home -->  
rm -rf .kube
rm -rf .minishift
--------------------------------------------------------------------------

openshift oc-env
export PATH="/home/erdnando/.minishift/cache/oc/v3.11.0/linux:$PATH"

The server is accessible via web console at:
    https://192.168.99.100:8443/console

You are logged in as:
    User:     developer
    Password: <any value>

To login as administrator:
    oc login -u system:admin