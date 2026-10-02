# Distributed System Metadata for Derivative Distributions #

Ships data and metadata that other packages consume but which changes on a
faster cadence than the code packages themselves, such as pinned known-good
version numbers and bundled signing keys.

Carrying this metadata in its own minimal, dependency-light package lets it be
updated and migrated between distribution suites independently of the heavier
code packages that would otherwise hold back such updates.

Each consumer gets its own namespaced subdirectory under
`/usr/share/dist-system-metadata/`, so the package is extensible to further
consumers beyond its initial `tb-updater` use case.

## How to install `dist-system-metadata` using apt-get ##

1\. Download the APT Signing Key.

```
wget https://www.kicksecure.com/keys/derivative.asc
```

Users can [check the Signing Key](https://www.kicksecure.com/wiki/Signing_Key) for better security.

2\. Add the APT Signing Key.

```
sudo cp ~/derivative.asc /usr/share/keyrings/derivative.asc
```

3\. Add the derivative repository.

```
echo "deb [signed-by=/usr/share/keyrings/derivative.asc] https://deb.kicksecure.com trixie main contrib non-free" | sudo tee /etc/apt/sources.list.d/derivative.list
```

4\. Update your package lists.

```
sudo apt-get update
```

5\. Install `dist-system-metadata`.

```
sudo apt-get install dist-system-metadata
```

## How to Build deb Package from Source Code ##

Can be build using standard Debian package build tools such as:

```
dpkg-buildpackage -b
```

See instructions.

NOTE: Replace `generic-package` with the actual name of this package `dist-system-metadata`.

* **A)** [easy](https://www.kicksecure.com/wiki/Dev/Build_Documentation/generic-package/easy), _OR_
* **B)** [including verifying software signatures](https://www.kicksecure.com/wiki/Dev/Build_Documentation/generic-package)

## Contact ##

* [Free Forum Support](https://forums.kicksecure.com)
* [Premium Support](https://www.kicksecure.com/wiki/Premium_Support)

## Donate ##

`dist-system-metadata` requires [donations](https://www.kicksecure.com/wiki/Donate) to stay alive!
