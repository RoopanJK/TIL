# Adding PPA to APT

- To add a [[ppa-personal-package-archive]] in APT (Advanced Package Tool) we use the `add-apt-repository` command followed by the PPA's address.

```
sudo add-apt-repository ppa:user/repository
```

- This add the PPA to our system's software sources.
- We have to then update the package lists so apt can find the new software.

```
sudo apt update
```