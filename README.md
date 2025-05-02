Geçersiz dosyayı silmek için:

sudo rm /etc/apt/sources.list.d/ubuntu.sources.curtin.orig
sudo apt-get update

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
