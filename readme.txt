1. Install Jack2 (route audio tool) http://jackaudio.org/. The following version seems to work fine in macOS 10.14:
	https://github.com/jackaudio/jackaudio.github.com/releases/tag/1.9.11

2. Install Darkice (audio streamer): `brew install darkice`

3. Darkice will be installed with Jack1 0.125.0 that doesn't seem to work so remove it: `brew uninstall --ignore-dependencies jack`

4. Install Icecast (internet radio server): `brew install icecast`

5. Prepare basic configs for Icecast and Darkice
	- note, in darkice config I changed the backend to jack_auto

6. Run Icecast: `icecast -c icecast.xml`
	- note, the path to icecast root is in the conf file and has to be corrected if homebrew upgrades it

7. Run Jack: `jackd -d coreaudio`

8. Run Darkice: `darkice -c darkice.cfg`
	- note, you can use `jack_lsp -c` to ensure that the audio interfaces were auto connected

Go to http://localhost:8000/admin/ and enter the admin-user (admin) and admin-password (hackme) from the icecast.xml config file.
You should arrive at the admin page.

Your stream is available via http://localhost:8000/spin