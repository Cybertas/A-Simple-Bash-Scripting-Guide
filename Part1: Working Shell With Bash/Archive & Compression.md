# Archive & Compression 
 - Compression can to applied to files to reduce their size.
 - Compression can be lossless, which the original data is preserved when reconstructed or lossy which the some information is discarded in the compression process.
 - Archiving is the process of gathering up multiple files and directories and building them together into a single large file. 
 - The purpose of archiving is to consolidate files for easier storage, organization and transportation. 
 - Archiving also preserves the file structure and metadata of the original files. 

 ## Compression 
 - The <code>gzip</code> command can be used to compress or expand files.
 - The <code>gunzip</code> command can be used to expand files. 
 - When executed, it replaces the original file with a compressed version of the original and vice versa. 

    ```bash
    ## create 3 test files
    dev@dev: echo "Test..." > test{1..3}
    
    ## compress a file, default behavior
    dev@dev: gzip test1 && ls
    test1.gz test2 test3

    ## compress files in a directory, using -r option
    dev@dev: gzip -r . && ls
    test1.gz test2.gz test3.gz

    ## decompress a file using gunzip
    dev@dev: gunzip test1.gz && ls
    test1 test2 test3

    ## decompress a file using -d option
    dev@dev: gzip -d test2.gz && ls
    test1 test2 test3.gz

    ## decompress files in a directory, using gunzip 
    dev@dev: gunzip -r . && ls
    test1 test2 test3
    ```


 ## Archive
 - Archiving is often done as part of system backups. 
 - The <code>tar</code> command can be used to archive files. 
 - File has **.tar** as filetype is an archived file and **.tgz** is zipped archived file.

    ```bash
   ## c, create and archive from a list of files or directories.
    ## x, extract an archive.
    ## t, list the contents of an archive. 
    ## f, specify the name of the file/directory

    ## create an archive
    ## tar [option] output input
   dev@dev: mkdir test_dir && echo "Test..." > test_dir/file{1..3} ## create a new directory 
   dev@dev: tar cf test_dir.tar test_dir
   dev@dev: ls
   test_dir test_dir.tar

    ## extract an archive
    dev@dev: rm test_dir && ls ## remove the original directory
    test_dir.tar
    dev@dev: tar xf test_dir.tar
    dev@dev: ls
    test_dir test_dir.tar

    ## list the contents of an archive
    dev@dev: tar tf test_dir.tar
    test_dir/
    test_dir/file3
    test_dir/file2
    test_dir/file1

    ## compress an archived file
    dev@dev: tar cfz test_dir.tgz test_dir

    ## decompress an archived file
    dev@dev: tar xfz test_dir.tgz
    ```