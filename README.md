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

	cd mantisbt-mysql # or another configuration
	vagrant up

MantisBT installation
---

Navigate to [http://localhost:8889/mantisbt/admin/]() and kick of the installation. 
The database username is _root_, password _toor_.

Enjoy!
