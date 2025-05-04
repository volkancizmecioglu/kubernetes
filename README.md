Geçersiz dosyayı silmek için:

sudo rm /etc/apt/sources.list.d/ubuntu.sources.curtin.orig

sudo apt-get update

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
IP adresini statik hale getirmek için:

Önce ip adresini öğreniyoruz:
ip a
(enpos'un nasıl yazıldığını not alın)

Netplan'ı açıyoruz:
cat /etc/netplan/01-netcfg.yaml

Sonra ip adresimizi tanımlıyoruz:

network:
  version: 2
  ethernets:
    enp0sx: #IP adresini kontrol ettiğinizdeki şekilde yazın
      dhcp4: no
      addresses:
        - xxx.xx.xx.x/xx #Statik hale getirmek istediğiniz IP adresini yazın
      gateway4: xxx.xx.xx.x #IP adresinizin gateway'ini tanımlayın
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Kubernetes Bileşenlerinin Kurulumu:

sudo apt update

sudo apt install -y apt-transport-https ca-certificates curl gpg

curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.28/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg

echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.28/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list

sudo apt update

sudo apt install -y kubelet kubeadm kubectl

sudo apt-mark hold kubelet kubeadm kubectl

kubectl version --client

kubeadm version

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
