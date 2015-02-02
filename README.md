# ResearchLink
Eine Vagrant Umgabeung basierend auf *Ubuntu Server 14.04.1 LTS*. Folgende Software wird zusätzlich installiert:

- R
- Ruby
- Python
- SDAPS
- LaTeX

## Installationshinweise

### 1. Vagrant

Installieren Sie Vagrant (http://www.vagrantup.com).

### 2. Vagrantfile anpassen

Kopieren oder klonen Sie das Vagrantfile und ändern Sie die Angaben für synchronisierte Ordner. Auf diese Weise können Sie einfach bestehende Projekte zugänglich machen.

    # Share an additional folder to the guest VM. The first argument is
    # the path on the host to the actual folder. The second argument is
    # the path on the guest to mount the folder. And the optional third
    # argument is a set of non-required options. Example Syntax:
    # config.vm.synced_folder "/Host/Folder/Path", "/Vagrant/Folder/Path"
    
    config.vm.synced_folder "~/Projects", "/home/vagrant/Projects"

### 3. Virtuelle Umgebung aufsetzen

Navigieren Sie in der Kommandozeile in das Verzeichnis in dem die Vagrantfile Datei gespeichert ist und führen Sie folgenden befehl aus:

    vagrant up

Der Installationsvorgang kann mehrere Minuten in Anspruch nehmen. Sobald er beendet ist können Sie sich über folgenden Befehl in der virtuellen Umgebung anmelden:

    vagrant ssh
    
Nun steht Ihnen eine wie zuvor beschrieben konfigurerte Linux Umgebung zur verfügung. D.h., die können z.B. folgende Befhele nutzen:

    R
    install.packages("FactoMineR");
    
## Proxykonfiguration

Sollten Sie gezwungen sein einen Proxy zu nutzen Sie bitte folgendes Plugin:

https://github.com/tmatilai/vagrant-proxyconf
