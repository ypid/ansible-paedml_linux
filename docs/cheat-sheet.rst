Cheat cheat
===========

.. contents::
   :local:

.. include:: includes/all.rst

Author‘s cheat cheat for setting up `paedML Linux`_ which you might find useful.
This can also be considered a TODO list of things which can potentially
be automated :)

Things to clarify with customer
-------------------------------

* Teacher/student user import.
* M$ licenses.
* Should the use of Thumb Drives be allowed for students? If yes, disable link GPO ``Musterloesung_Wechselmedienzugriff_W7``.

Things to remember
------------------

* Run in ``screen``:

  .. code-block:: console

     univention-upgrade --ignoressh

* Import Root CA certificate into the dedicated browser profile you are using for the environment.

* Change ``system_partition_size`` to at least 70 GB to have space to install a few applications.
  (Side note: The applications to install are still nothing compared to the software list put together for a `Ubuntu GNU/Linux client in a linuxmuster.net environment <https://github.com/ypid/ansible-linuxmuster_net_client>`_)

* In case there are computers in the mix with less than 200 GiB in capacity,
  consider adopting the ``minimal_backup_parition_size`` parameter
  appropriately. So it might not be possible to do a local backup for those
  computers.

* If there is a upstream Proxy server provided, use it by writing for example
  ``cache_peer wwwproxy.belwue.de parent 8080 3130 default no-query`` into
  :file:`server:/etc/squid3/local.conf`.

.. * To allow to connect to non-default http ports.
     Commented out ACL '# http_access deny !web_ports' in server:/etc/squid3/squid.conf

     Will break on update.

Printing
~~~~~~~~

Setting up printing can be confusing. Some hints.

* Optional: Do initial setup (before X.509 certificates have been regenerated and saved)
  on a peer-to-peer connection.

* Read printer vendor, model and details via SNMP: :command:`/usr/lib/cups/backend/snmp $printer_name`.

* Printing protocol preference

  #. IPP over SSL/TLS; printers for which I could not get this to work

     * Kyocera ECOSYS P6021cdn
       cups: 1.7.5-11+deb8u1
       device system fw version: 2PT_3F00.003.021
       device engine fw version: 2PS_1000.003.001

       With ``encryption=required`` e. g. TLS required, the device sent a TCP
       reset after Cups tried a connection upgrade to TLS via HTTP options.

  #. AppSocket

* PPD files can be copied to: :file:`/usr/share/ppd/eigene-treiber/` on the main server.

* Printers can be setup in the adminvm using :program:`printmanagement.msc`.

* If the printing drivers for Microsoft Windows or Microsoft printing servers
  are somehow wired, try ignoring them and use "MS Publisher Color Printer". Cups
  should be able to do the conversion.

* Generic device security: Set language to English (translation can be confusing).
  Set admin password.
  Set hostname.
  Regen X.509 certificate.
  Enable HTTPS, IPP(s), and AppSocket.
  Disallow or change SNMP write community. Leave SNMP read as is as this might be useful for Monitoring and is also used by cups.
  Lock the operation panel.
  Disable every unneeded protocol or service like HTTP, SMTP, zeroconf, Google Cloud Print, AirPrint and so on.

* Device security hardening. Because the printer firmware is expected to have
  bugs and school networks can not be trusted, setup some kind of IP filter on
  the device to only allow access from the IP address of the main server.
  This also hides things like job history which some printers seem to expose via the web interface.
  The web interface can be accessed via an TCP tunnel over the main server via SSH and :command:`ncat`.
  Other/additional possibilities (probably overkill): IEEE 802.1X, VLAN, Firewall.

* Setup two printers for one physical printer and limit one of them to only
  black and white (gray scale) printing.  This should make it easier to manage
  color printing via the school console.

* Restrict access to Cups to not expose print job history and unlimited access to printers by editing
  :file:`/etc/cups/cupsd.conf`. TODO: Check if user authentication makes sense.

  .. warning:: It seems paedML Linux does not configure Cups on the main server to enforce the printer to
     room mappings at all! Just add the printer on another Cups server via
     ``https://server.paedml-linux.lokal:631/printers/$printername`` and the main
     server happily printers your jobs unless you restrict it as suggested.


Default passwords
-----------------

``adminvm``
  Administrator: nt123

``opsi-boot-image``
  root: linux123

  Hint: You can also login to it via SSH :)

Remote access
-------------

You really want to go the OpenVPN route because the OpenSSH version installed
is very old (OpenSSH_5.5p1 Debian-6.55.201601151048, OpenSSL 0.9.8o 01 Jun
2010) in terms of cyphers it supports.

OpenVPN in the default configuration of the paedML Linux does also not use the
strongest cyphers out there.
