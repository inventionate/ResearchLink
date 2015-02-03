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
  config.vm.synced_folder "Projects/Folder", "/home/vagrant/Folder"

  # Proxy configration
  # if Vagrant.has_plugin?("vagrant-proxyconf")
  #   config.proxy.http     = "http://proxy.ph-karlsruhe.de:3128/"
  #   config.proxy.https    = "http://proxy.ph-karlsruhe.de:3128/"
  #   config.proxy.no_proxy = "localhost,127.0.0.1,.example.com"
  # end

  # Additional software.
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    # LaTeX installieren
    sudo apt-get install -y texlive-latex-recommended texlive-latex-extra texlive-fonts-recommended texlive-lang-german texlive-math-extra pgf
    # Ruby installieren
    sudo apt-get install -y ruby
    # Alle Python Abhängigkeiten für SDAPS installieren
    sudo apt-get -y install python-distutils-extra python-cairo-dev libtiff5-dev libcairo2-dev libglib2.0-dev python2.7-dev python-zbar python-gi python-gi-cairo gir1.2-gtk-3.0 python-pypdf python-reportlab python-imaging gir1.2-poppler-0.18 python-opencv
    # SDAPS installieren
    sudo add-apt-repository "http://ppa.launchpad.net/benjamin-sipsolutions/sdaps/ubuntu trusty main"
    sudo apt-get update
    sudo apt-get install -y sdaps --force-yes
    # SDAPS LaTeX Dateien kopieren
    DIR="$(kpsewhich -expand-var '$TEXMFDIST')/tex/latex"
    sudo mkdir $DIR/sdaps
    sudo cp -R /usr/share/sdaps/tex/* $DIR/sdaps
    # # PaperAndPencil installieren
    # wget http://www.qdds.de/fileadmin/files/latexstyles.zip
    # unzip latexstyles.zip
    # rm -rf PAPI
    # sudo mkdir $DIR/paperandpencil
    # sudo cp ~/PaperAndPencil/paperandpencil.sty $DIR/paperandpencil
    # rm -rf PaperAndPencil
    # rm -rf latexstyles.zip
    # LaTeX aktualisieren
    sudo texconfig rehash
    # R Installieren
    sudo apt-get install -y r-base
  SHELL

end
