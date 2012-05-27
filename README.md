nagios-check-http-multi-ips
===========================

This plugin is aimed to monitor multiple IP addresses for HTTP for the domain who has multiple A records.

USAGE EXAMPLE
-------------

If you want to check www.google.com's A records with P06C UserAgent:

    check_http_multiips -hostname www.google.co.jp -check-http /usr/local/nagios/libexec/check_http \
                        -warning 2 -critical 4 -- -A 'DoCoMo/2.0 P06C(c500;TB;W24H16)'

EXAMPLE of perlbrew and nagios
------------------------------

Nagios does not seem to evaluate `source perlbrew-bashrc`.
If you set up Perl environment with perlbrew, you can use a command definition like the following:

    define command{
            command_name    check_http_multi
            command_line    PATH=/home/nagios/perl5/perlbrew/bin:/home/nagios/perl5/perlbrew/perls/perl-5.15.9/bin \
                            /home/nagios/git/nagios-check-http-multi-ips/check_http_multiips \
                            -hostname $HOSTADDRESS$ -check-http $USER1$/check_http -warning 1 -critical 4 -- $ARG1$
    }


