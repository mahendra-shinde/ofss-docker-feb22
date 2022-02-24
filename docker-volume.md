# Docker Volumes

Volumes are `persisted storage` for container, Have disjoined lifecycle (deleting container will have no effect on volume).

* A Single container can have any number of volumes.
* Multiple Containers can `share` volume.
* For `A Container`, a volume is just a `folder path`.
    
    Whenever any changes are detected inside container filesystem, docker (container runtime) will check if changes are MADE inside volume? is NO, then changes are recorded to Writable layer.

Volume Types:

1.  Named Volumes

    - Volumes created using `docker volume create`
    - These values can be Easily shared between containers.
    - Volumes are STORED in PROTECTED Directory to avoid accidental changes from Host OS.


2.  Volume Bindings / Host Binding

    - Assign EXISTING folder path from HOST OS directly as Volume
    - Data inside volume can be modified out container.

### Demo : A MySQL Sample Database using Volumes

1.  Create a named volume

    ```
    docker volume create dbvol
    ```

2.  Create the container

    ```
    docker run -d -v dbvol:/var/lib/mysql --name db1 -e MYSQL_DATABASE=sample \
        -e MYSQL_USER=mahendra -e MYSQL_PASSWORD=pass@1234 \
        -e MYSQL_ROOT_PASSWORD=pass@1234 \
        mysql:5.7

    ```

3.  View the database logs (after 30 seconds)

    ```
    docker logs db1
    ```

4.  Get INSIDE the container, to create table:

    ```
    docker exec -it db1 bash
    mysql -umahendra -ppass@1234 
    use sample;
    create table emp ( empid int primary key, ename varchar(20) );
    insert into emp values (101, 'Pluto' );
    insert into emp values (102, 'ceres');
    commit;
    exit
    exit
    ```
5.  Delete and recreate the container

    ```
    docker stop db1
    docker rm db1
    docker run -d -v dbvol:/var/lib/mysql --name db1 -e MYSQL_DATABASE=sample \
        -e MYSQL_USER=mahendra -e MYSQL_PASSWORD=pass@1234 \
        -e MYSQL_ROOT_PASSWORD=pass@1234 \
        mysql:5.7
    ```

6.  Get inside to test the previous data

    ```
    docker exec -it db1 bash
    mysql -umahendra -ppass@1234 
    use sample;
    select * from emp;
    exit
    exit
    ```