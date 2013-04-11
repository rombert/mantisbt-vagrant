MantisBT vagrant configurations used for QA
===

As an experiment, I'm trying to quickly spin up MantisBT instances with
different configurations which can be used for testing the latest code
checked in to git.

Usage
---

Bootstrap the needed external cookbooks

	knife cookbook site download apache2  
	knife cookbook site download git
	knife cookbook site download mysql
	knife cookbook site download openssl
	knife cookbook site download php
	for cookbook in $(ls *.tar.gz); do tar xf $cookbook -C cookbooks && rm -f $cookbook; done

Initialise the internal cookbooks

	git submodule init
	git submodule update

Run the machine

	vagrant up
