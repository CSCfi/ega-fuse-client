# EGA FUSE Client

This is a Java-(JNR)-based FUSE client for the EGA Data REST API (v3). This client will allow access to authorized EGA Archive files by presenting them in a vitual directory, where then can be used like regular files, without first having to download them.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine.

### Installing

The repository contains pre-compiled jar files with the client. To build it on your local machine, run

```
mvn package
```

This will produce the FUSE later jar file in the /target directory.

## Starting the FUSE layer

The FUSE layer requires at minimum a valid EGA OAuth2 Bearer Token to run; specifying a mount directory is recommened (default is /tmp/mnt). The mount directoty must be an existing and empty directory:

```
java -jar EgaFUSE-1.0-SNAPSHOT.jar -t {bearer token} -m {mount dir}
```

This will populate the {mount dir} with a directory called "Datasets". To view all datasets to which the OAuth2 token provides access:

```
cd Datasets
ls
```

Running 'ls' or 'll' will populate the directory, otherwise the Datasets directory will be empty (it is not possible to directly cd into a Dataset directory upon starting the FUSE client, because it will have to be populated first).

The same procedure then applies to Dataset directories. Change into a dataset, then run 'ls' or 'll' to populate the directory. Now all files listed in the directory can be used like norman file system files.

## License

This project is licensed under the Apache 2.0 License - see the [LICENSE.md](LICENSE.md) file for details

