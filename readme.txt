Usage
=====
  mozillapackager_univ.py [options]
 or 
  python mozillapackager_univ.py [options]

The Mozillapackager script can install the official Mozilla build of Firefox,
Thunderbird, or Seamonkey, on an Ubuntu Linux system, in parallel with any
existing versions from the repositories and make the also the *.deb. 
Options
=======
--version               show program's version number and exit
--help, -h              show this help message and exit
--debug, -d             debug mode (print some extra debug output). [default:
                        False]
--test, -t              make a dry run, without actually installing anything.
                        [default: False]
--package=PACKAGE, -p PACKAGE
                        which package to work on: firefox, thunderbird, or
                        seamonkey. [default: firefox]
--action=ACTION, -a ACTION
                        what to do with the selected package: builddeb creates
                        the .deb; adddebtorepo updates the repository;
                        uploadrepo uploads the repository; cleanup removes
                        temporary files; all does all of this from start to
                        finish. [default: all]
--skipgpg, -g           skip gpg signature verification. [default: True]
--unattended, -u        run in unattended mode. [default: False]
--localization=LOCALIZATION, -l LOCALIZATION
                        for use with unattended mode only. choose localization
                        (language) for your package of choice. note that the
                        burden is on you to make sure that this localization
                        of your package actually exists. [default: en-US]
--debversion=DEBVERSION, -v DEBVERSION
                        The ubuntu-version of the package to create. To be
                        used in case a bad package was pushed out, and users
                        should be upgraded to a fresh repack. [default: 1]
--debdir=DEBDIR, -b DEBDIR
                        Directory where to stick the completed .deb file.
                        [default: /home/<user_id>/Scrivania/mozillapackager]
--targetdir=TARGETDIR, -r TARGETDIR
                        installation/uninstallation target directory for the
                        .deb. [default: /opt]
--mirror=MIRRORS, -m MIRRORS
                        Prepend a mozilla mirror server to the default list of
                        mirrors. Use ftp mirrors only. Include path component
                        up to the 'firefox', 'thunderbird', or 'seamonkey'
                        directories. (See http://www.mozilla.org/mirrors.html
                        for list of mirrors). [default:
                        ['mozilla.isc.org/pub/mozilla.org/',
                        'mozilla.ussg.indiana.edu/pub/mozilla.org/',
                        'ftp.osuosl.org/pub/mozilla.org/',
                        'mozilla.cs.utah.edu/pub/mozilla.org/',
                        'mozilla.mirrors.tds.net/pub/mozilla.org/',
                        'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-
                        erlangen.de/pub/mozilla.org/',
                        'sunsite.rediris.es/pub/mozilla.org/',
                        'www.gtlib.gatech.edu/pub/mozilla.org/',
                        'releases.mozilla.org/pub/mozilla.org/']]
--keyservers=KEYSERVERS, -k KEYSERVERS
                        Prepend a pgp keyserver to the default list of
                        keyservers. [default: ['subkeys.pgp.net',
                        'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net',
                        'keymaster.veridis.com']]

--------------------------------------------------------------------------------------------------------

V. 1.0

Avendo necessità di realizzare i pacchetti *.deb di firefox e thujnderbird per uso personale ho modificato lo script originario di 
nanotube per avere le versioni localizzate in italiano o in qualsiasi altra lingua (in modo tale da non dovere scaricare la versione in inglese,
scaricare il langpack italiano e poi cambiare la stringa del general.useragent.locale. Lo script scarica i binari dei programmi e realizza i *.deb.
Ricordatevi di controllare il locale per la vostra versione qui :

http://releases.mozilla.org/pub/mozilla.org/firefox/releases/4.0/linux-i686/
http://releases.mozilla.org/pub/mozilla.org/firefox/releases/4.0/linux-x86_64/
http://releases.mozilla.org/pub/mozilla.org/firefox/releases/latest-3.6/linux-i686/
http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/3.1.9/

ad esempio. Il path è simile per le altre versioni ovviamente. Lo script scaricherà sempre l'ultima versione dei binari a meno che alla prima domanda 
che vi viene posta rispondiate 'n' e successivamente inseriate il numero della versione.

Qui di sopra ho riportato le opzioni dell' "help" dello script. Non c'è niente di difficile nell'uso

es:

python mozillapackage_univ.py -l it (per l'ultima versione di firefox in italiano)
python mozillapackage_univ.py -l it -p thunderbird (per l'ultima versione di thunderbird in italiano)
python mozillapackage_univ.py -l it -p seamonkey (per l'ultima versione di seamonkey in italiano)

Per quanto riguarda lo script per le versioni a 64 bit, attualmente esistono solo i binari Firefox 4 a 64 bit. Pertando chi vuole
i vantaggi dei 64 bit per una versione precedente di Firefox od una attuale di Thunderbird o sfrutta i repository di ubuntu oppure
compila da sorgente i programmi, altrimenti installa i pacchetti con architettura i386 così generati con 

sudo dpkg -i --force-architecture <nome-pacchetto>

ricordatevi però di avere installato il pacchetto "ia32-libs".

Le prossime versioni di thunderbird a quanto pare saranno pure a 64 bit quindi in seguito correggerò lo script per avere un totale controllo sui
binari a 64 bit.
 
E' tutto :D !

-----------------------------------------------------------------------------------------------------------

V. 2.2

+piccoli cambi agli url interni dello script

V. 2.0

+Il "locale" di default adesso è l'Italiano (it)
+aggiunto il mirror ftp://ftp.mozilla.org/pub/ da cui prendere le versioni beta dei programmi
+aggiunto il supporto per thunderbird a 64 bit

uso tipico :

python mozillapackager_univ_x86_2.0.py (per l'ultima versione di firefox in italiano)
python mozillapackager_univ_x86_2.0.py -p thunderbird (per l'ultima versione di thunderbird in italiano)
python mozillapackager_univ_x86_2.0.py -p seamonkey (per l'ultima versione di seamonkey in italiano (SOLO x86))

python mozillapackager_univ_x64_2.0.py (per l'ultima versione di firefox in italiano X64)
python mozillapackager_univ_x64_2.0.py -p thunderbird (per l'ultima versione di thunderbird in italiano X64)

-----------------------------------------------------------------------------------------------------------

Per qualsiasi domanda, commento o suggerimento non esitate a contattarmi a questo indirizzo email :

arty.net2@gmail.com
