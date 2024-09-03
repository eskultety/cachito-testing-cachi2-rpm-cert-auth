# cachi2-rpm-cert-auth

Generate lockfile:
First build conainer
podman build -t rpm-lockfile .

then create a rpms.in.yaml
ensure the IP addr of the repo is reachable. 
if using containers you may need to sepcify the real IP of the host, not the loopback

To generate a lockfile:
podman run -v $(pwd):$(pwd) \
  --rm rpm-lockfile \ 
  --outfile $(pwd)/rpms.lock.yaml \
  $(pwd)/rpms.in.yaml

Run just this test with:
tox -e integration -- tests/integration/test_rpm.py::test_rpm_packages[rpm_cert_auth]
