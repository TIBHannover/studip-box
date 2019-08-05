# studip-box

Dieses Projekt bietet die Möglichkeit, ein studip mit minimalem Aufwand in einer virtuellen Maschine aufzusetzen. Voraussetzung ist die Installation von
[Git](https://git-scm.com/downloads),  [Vagrant](https://www.vagrantup.com/downloads.html) und [VirtualBox](https://www.virtualbox.org/wiki/Downloads).

## Installation

Die folgenden Schritte im Terminal (Linux/macOS) oder in der GitBash (Windows) ausführen.
```
git clone https://github.com/TIBHannover/studip-box.git
cd studip-box
vagrant up
```
Wenn die Installation durchgelaufen ist (einige Minuten, abhängig von der Download-Geschwindigkeit) kann studip im Browser aufgerufen werden mit

<http://192.168.98.107/studip>

Die Anmeldung an studip erfolgt mit root@studip/testing

In Stud.IP werden Demo-Daten (Veranstaltungen/Accounts) eingespielt. Dies kann ausgeschaltet werden indem man im Vagrantfile "ansible.skip_tags = [ "demo-data" ]" aktiviert. Folgende Zugänge gibt es für die Demo-Accounts:
* test_admin/testing
* test_dozent/testing
* test_tutor/testing
* test_autor/testing

Die Anmeldung an der VM via SSH erfolgt in diesem Beispiel noch vereinfacht und ohne Passwort mit dem Benutzer "vagrant". Der Benutzer hat das sudo-Recht.
```
vagrant ssh
```
