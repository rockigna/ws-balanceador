Vagrant.configure("2") do |config|
    ### este es el balanceador
        config.vm.define "balanceador" do |balanceador|
            balanceador.vm.box = "hashicorp/precise64"
            balanceador.vm.hostname = "balanceador"
            balanceador.vm.network "private_network", ip:"192.168.100.100"
            balanceador.vm.provider "virtualbox" do |v|
                v.memory = 512
                v.cpus =2
            end
        end                                                              

### este es la primera web 
### primera
        config.vm.define "primera" do |primera|
            primera.vm.box = "hashicorp/precise64"
            primera.vm.hostname = "primera"
            primera.vm.network "private_network", ip: "192.168.100.101"
            primera.vm.provider "virtualbox" do |v|
                v.memory = 512
                v.cpus = 2
            end
        end

### esta es la segunda web (clon de la primera)
### los datos se transfieren 50/50
### se va a llamar segunda
         config.vm.define "segunda" do |segunda|
            segunda.vm.box = "hashicorp/precise64"
            segunda.vm.hostname = "segunda"
            segunda.vm.network "private_network", ip: "192.168.100.102"
            segunda.vm.provider "virtualbox" do |v|
                v.memory = 512
                v.cpus = 2
            end
        end
    end