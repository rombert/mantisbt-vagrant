MantisBT vagrant configurations used for QA
===

As an experiment, I'm trying to quickly spin up MantisBT instances with
different configurations which can be used for testing the latest code
checked in to git.

Usage
---

Bootstrap the needed external cookbooks

	for cookbook in 'apache2 git mysql openssl php apt'; do knife cookbook site download $cookbook; done
	for cookbook in $(ls *.tar.gz); do tar xf $cookbook -C cookbooks && rm -f $cookbook; done

Initialise the internal cookbooks

	git submodule init
	git submodule update

Run the machine

	vagrant up
