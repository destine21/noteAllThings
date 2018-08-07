Directory fuzzing
===
wfuzz -c -z file,directory-list-2.3-medium.txt --hc="404" -Z https://www.xxx.com/FUZZ

--hc="404" hide http response code 404
--hw="100" hide word (number of chars)
---