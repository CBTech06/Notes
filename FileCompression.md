# ---- [COMPRESSSION] ----
                        
               < [index]

# ZIP

   * Usage: zip <file.zip> *.c *.h
                
   Recursive zip with folder 
   zip -r <file.zip> Folder/*

## UNZIP

   * Usage: unzip [options] filename>

   Options:
    -d /path/location               Unzip to a different directory
    -j                              Unzip without creating new folder 
    -l                              Lists the contents of an archive without extracting it
    -P password                     Supplies a password to unzip protected archive
    -t                              Test whether a file is valid
    -x filename                     Extract 

## 7ZIP

  * Compress files or directory with password
         7z a secret.7z <file/dir> -pSECRET

  * unzip file:
        7z x <file.7z>

## TAR

  * Usage: tar -[options] file.tar.gz

  * Options:
     -c                              Create an archive
     -x                              Extract a tar ball
     -v                              Verbose
     -f                              Specify an archive or a tarball filename
     -j                              Decompress
     -z                              Decompress/extract the content of compressed 
                                     archive create by gzip(gz)

    Extract tgz file                                  tar -xvf filename.tgz
    Extract tar.gz file                               tar -zxvf filename.tar.gz
    Extract tar.bz2 file                              tar -jxvf filename.tar.bz2
    Extract tar.xz (need xz pkg)                      tar -xvf guitarix2.tar.xz 
    Extract into a different directory : 

    tar -zxvf filename.tgz -C <directory>
    tar -zxvf filename.tar.gz <directory>
    tar -jxvf filename.tar.bz2 <directory>

    * Compress an entire directory or single file: tar -czvf archive.tar.gz /folder

    * Compress Multiple directories or File at once
                        tar -czvf archive.tar.gz /home/ubuntu/Downloads 
                                                 /usr/local/stuff 
                                                 /home/ubuntu/Documents/notes.txt
