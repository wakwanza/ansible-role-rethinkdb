Ansible Role: Rethinkdb
=========

An Ansible Role that installs RethinkDB on RedHat/CentOS,Debian/Ubuntu or Archlinux.


Requirements
------------

Works on Linux versions based on Enterprise Linux (CentOS/RedHat >=6), Debian (jessie & wheezy) and Ubuntu (>=precise).
On EL based distributions SELINUX needs to be set to permissive for some of the tasks to work.

Role Variables
--------------

<table>
    <tr>
        <td>`storage_directory_base`</td> <td>Directory root to store data and metadata.Defaults to /var/lib/rethinkdb</td>
    </tr>
        <tr>
        <td>`storage_data`</td> <td>RW Directory to store data and metadata.Defaults to 'data' to create {{ storage_directory_base }}/data </td>
    </tr>
    <tr>
        <td>`port.driver`</td> <td>The port for rethinkdb protocol for client drivers.Defaults to '28015'</td>
    </tr>
    </tr>
    <tr>
        <td>`port.cluster`</td> <td>The port for receiving connections from other nodes.Defaults to '29015'</td>
    </tr>
    <tr>
        <td>`port.offset`</td> <td>All ports used locally will have this value added.Defaults to '0'</td>
    </tr>
     <tr>
        <td>`server_tag`</td> <td>Tag name usable to identify groupings for sharding etc.Defaults to 'nyc'</td>
    </tr>
    <tr>
        <td>`io_threads`</td> <td> How many simultaneous I/O operations can happen at the same time.Defaults to '64'</td>
    </tr>
    <tr>
        <td>`cluster_lead`</td> <td>The ipv4 address for the initial leader.If not set defaults to pick first host that role will run on.</td>
    </tr>
</table>

For secure installation the web-admin interface is disabled , nodes listen to the default intefaces's ipv4 address.The number of cores used is the total available in each node and the memory cache available is set at 0.85 of the total available RAM.
Further tuning possible by modifying values in 'templates/rethinkdb.j2'.

Example Playbook
----------------

Install the role using galaxy : ansible-galaxy install wakwanza.rethinkdb

    - hosts: nosqldb
      roles:
         - { role: wakwanza.rethinkdb }

License
-------

MIT

Author Information
------------------

@wakwanza Abdulrahim Umar.
