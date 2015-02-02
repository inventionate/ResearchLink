# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080


  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "~/Matrix/Dissertation", "/home/vagrant/Dissertation"
  config.vm.synced_folder "~/Matrix/Inventionate", "/home/vagrant/Inventionate"

  # Additional software.
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    # LaTeX installieren
    sudo apt-get install -y texlive-latex-recommended texlive-latex-extra texlive-fonts-recommended texlive-lang-german pgf
    # Ruby installieren
    sudo apt-get install -y ruby
    # Alle Python Abhängigkeiten für SDAPS installieren
    sudo apt-get -y install python-distutils-extra python-cairo-dev libtiff5-dev libcairo2-dev libglib2.0-dev python2.7-dev python-zbar python-gi python-gi-cairo gir1.2-gtk-3.0 python-pypdf python-reportlab python-imaging gir1.2-poppler-0.18 python-opencv
    # # SDAPS installieren
    sudo add-apt-repository "http://ppa.launchpad.net/benjamin-sipsolutions/sdaps/ubuntu trusty main"
    sudo apt-get update
    sudo apt-get install -y sdaps --force-yes
    DIR="$(kpsewhich -expand-var '$TEXMFDIST')/tex/latex"
    sudo mkdir $DIR/sdaps
    sudo cp -R /usr/share/sdaps/tex/* $DIR/sdaps
    sudo texconfig rehash
    # R Installieren
    sudo apt-get install -y r-base
  SHELL


  # R Packete konfiguirieren
  # Shellskript laden und als R Skript ausführen.
  # #!/usr/bin/r

end
