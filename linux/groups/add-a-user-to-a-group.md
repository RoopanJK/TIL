# Add a User to a Group

- User usermod to modify groups.
```
sudo usermod -a -G *your-group* *your-user*
```
- The -a switch is required here to append with the group. Else it will be overwritten.
- the -G switch represents group.