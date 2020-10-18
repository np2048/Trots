
# sed — stream editor for filtering and transforming text

Using *sed* you can manipulate text strings right in the Linux terminal command line.

## Replace

This command will cut all the spaces into a string (replace spaces with nothing):

    $  echo '04BB 537F 5BC2 D399 BFA7  2F8F 17C7 52B6 1B2F 2E90' | sed 's/ //g'
    04BB537F5BC2D399BFA72F8F17C752B61B2F2E90