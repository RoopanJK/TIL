# Text Insertion into File via HereDoc Input Stream

- Multi line strings can be inserted into files via the following command.
- heredoc preserves line breaks and empty spaces.
- The delimiter is used as a reference.
```
cat << EOF > *your-text-file-path*
Your Multiline
string with line
break and white   spaces
EOF
```
- Here `EOF` is used as a delimiter. It can be anything as long as both match.