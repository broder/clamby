#v1.0.5
 - Made default virus detection not throw a warning
 - If scanning a file that doesn't exist, `scan(path)` will return nil.
 - If scanning a file where `clamscan` doesn't exist, `scan(path)` will return nil.
 - Added test for nil result on scanning a file that doesn't exist

#v1.0.4
 - Added tests. This WILL download a file with a virus signature. It is a safe file, but is used for the purposes of testing the detection of a virus. Regardless, use caution when running rspec as this could be potentially harmful (doubtful, but be warned).

```ruby
.ClamAV 0.98.1/18563/Sun Mar  9 17:39:31 2014
.FILE NOT FOUND on 2014-03-10 21:35:44 -0400: BAD_FILE.md
.ClamAV 0.98.1/18563/Sun Mar  9 17:39:31 2014
README.md: OK
.--2014-03-10 21:35:50--  http://www.eicar.org/download/eicar.com
Resolving www.eicar.org... 188.40.238.250
Connecting to www.eicar.org|188.40.238.250|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 68 [application/octet-stream]
Saving to: 'eicar.com'

100%[=================>] 68          --.-K/s   in 0s      

2014-03-10 21:35:50 (13.0 MB/s) - 'eicar.com' saved [68/68]

ClamAV 0.98.1/18563/Sun Mar  9 17:39:31 2014
eicar.com: Eicar-Test-Signature FOUND
ClamAV 0.98.1/18563/Sun Mar  9 17:39:31 2014
eicar.com: Eicar-Test-Signature FOUND
VIRUS DETECTED on 2014-03-10 21:36:02 -0400: eicar.com
.

Finished in 17.79 seconds
5 examples, 0 failures
````

 - Changed `scanner_exists?` method to check `clamscan -V` for version instead of just `clamscan` which was causing a virus scan on the local folder. This ended up throwing false checks since I had a virus test file in the root of the directory.

 #v1.0.3
  - Added exceptions
  - New configuration options

```ruby
Clamby.configure({
   :check => false,
   :error_clamscan_missing => false,
   :error_file_missing => false,
   :error_file_virus => false
})

```