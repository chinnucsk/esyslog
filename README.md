esyslog: Simple interface to syslog
===================================

Sample configuration
--------------------

<pre>
[
    {esyslog, [
        {server, {127, 0, 0, 1}},
        {port, 514}
    ]}
].
</pre>

Sample syslog-ng configuration
------------------------------

<pre>
destination d_mylog {
    file("/var/log/my.log");
};

source s_net {
    udp();
};

log {
    source(s_net);
    destination(d_mylog);
};
</pre>

Sample rsyslog configuration
----------------------------

<pre>
$ModLoad imudp
$UDPServerRun 514

if $programname == 'YOUR_PROGRAM' then /var/log/your_program.log
</pre>

LICENSE
-------

Some code was taken from https://github.com/lemenkov/erlsyslog
