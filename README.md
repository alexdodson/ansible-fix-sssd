# ansible-fix-sssd

This role creates a 128M mount of tmpfs for /var/lib/sss/db to improve the performance of SSSD as it fsyncs all the time. This impacts authentication and sudo greatly on virtual machines especially when running on network based storage like ceph rbd devices. Even when you disable caching it still does many fsyncs anyway...

There are some intial checks to the role to also clean up a workaround I had in place temporarily on some machines. You can edit them out if you like but they won't cause the role to fail. The mount command and the restart of sssd are all that is important.

This was tested on RHEL6
