# Base role

The base role handles installation and updating of the standard 
packages `apt`, `build-essential`, and `systemd`. It also ensures
that users and groups are installed. By default, a `sysadmin` group
with passwordless sudo access is created.

The packages, users, and groups defined in `vars/main.yml` will be
installed on every host using the role. Extra users, groups, and
packages can be defined as follows:

* Packages

    ```yml
    extra_packages:
      Ubuntu:
      - {name: <pkg_name>, state: <pkg_state>}
      - {name: <pkg2_name>, state: <pkg2_state>}
    ```

* Users

    ```yml
    # Note that non-login users can be added with the same syntax
    # using the key `non_login_users`
    extra_login_users:
    - name: <username>
      key: <ssh public key>
      state: present
      createhome: yes
      groups: <comma-separated groups>
    ```

* Groups

    ```yml
    extra_groups:
    - name: <group name>
      sudo: <boolean>
      state: present
    ```

You can run `ansible-doc group`, `ansible-doc user`, and
`ansible-doc apt` for more information.
