
**For the key issues**

`gpg --keyserver pool.sks-keyservers.net --recv-keys 95D2E9AB8740D8046387FD151A09227B1F435A33`

**Install reflector for Updating fast mirrorlist**

`sudo pacman -Syy reflector`

**Wifi Settings**
1. `iwctl`
2. `wsc list` to find wifi device
3. `wsc wlan0* push-button`
4. `station wlan0* scan`
5. `staton wlan0* get-networks`
6. `station wlan0* connect elrod*`
