py-text
=======
A suite text tools for python

Installation
------------
The lastest stable is py-text-1.2.tar.gz

    python setup.py install
    
## Getting Start ##

awk demo for py-text:

	from text import awk
	data = ['root:x:0:0:root:/root:/bin/bash',
			'daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin',
			'bin:x:2:2:bin:/bin:/usr/sbin/nologin']
	resut = awk.awk(data, None, ':', [0,4,5])
	print result

	[['root', 'root', '/root'], ['daemon', 'daemon', '/usr/sbin'], ['bin', 'bin', '/bin']]

string_utils demo for py-text:

	from text import string_util
	print 'substring_before : ' + string_utils.substring_before('one world one dream', 'one dream').strip() + '\n'
	print 'abbreviate : ' + string_utils.abbreviate('abcdef', 3, 3) + '\n'
	print 'count_matches : ' + string_utils.count_matches('one world one dream', 'one') + '\n'

	substring_before : one world
	abbreviate : abc***
	count_matches : 2

regex_utils demo for py-text:

	from text import regex_util
	print 'check_line : ' + regex_utils.check_line('.*(\d+.\d+.\d+.\d+)', 'MyIP is 192.168.199.4') + '\n'
	print 'parse_line : ' + str(regex_utils.parse_line('name=(\S+), type=(\S+)', 'name=ASA5505, type=Firewall)) + '\n'

	check_line : True
	parse_line : ['ASA5505', 'Firewall']
	
edit demo for py-text:

edit script:

	[test_file/interface_config]
	# Delete Comment line
	D:/1-3, 4, 8/
	# Update eth0 to static
	U:iface eth0.*->iface eth0 inet static
	# Add eth1 to dhcp
	A:[:end]->[:lf]
	A:[:end]->auto eth1[:lf]iface eth1 inet dhcp
	# Add header
	A:[:start]-># network interface config
	# Add Footer
	N:# end of config

program:

	from edit import edit
	edit.edit('script_file/edit.script')
	
Documentation
------------

Full documentation is hosted on [HERE](). 
Sources are available in the `docs/` directory.

License
-------
py-text is licensed under the Apache License, Version 2.0. See LICENSE for full license text