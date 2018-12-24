# macports

Ports not found in the official repository.

## Using a Local Repository

```
repo="~/Repos/macports.git"
mkdir -p $repo
git clone git@github.com:thrivedata/macports.git $repo
sudo -s eval 'echo "file:///$repo" >> /opt/local/etc/macports/sources.conf'
cd $repo
portindex
sudo port install libasr
```

To check the local repo first, move the new line in `sources.conf` to the top.

https://guide.macports.org/#development.local-repositories

## Port Notes

#### opensmtpd

This port is not compatible with **openssl** and must use **libressl**.
Because **libressl** is a drop-in replacement for **openssl**, they conflict with each other.
If you have **openssl** installed already:

```
sudo port uninstall -f openssl
sudo port install libressl
sudo port rev-upgrade
```

Use caution with the above commands, YMMV.
