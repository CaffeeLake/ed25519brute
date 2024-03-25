# ed25519brute

> [!CAUTION]
> This is a joke software. Do not use SSH keys generated by this software. Use `ssh-keygen` instead.

ed25519brute brute-forces ed25519 public key with a given authorized key suffix or fingerprint prefix/suffix.

Here is an example of ed25519 public key with authorized key prefix of A, fingerprint prefix of A, and suffix of A.

```
% cat out.pub
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIGFFEo+qnsDoIo8DyNMgr1HoqPM89yMc6mrzWdFIc4vA
% ssh-keygen -l -f out
256 SHA256:AEV1jYsPpgx6Gqik2Z4NMOUHVUc/mRD6aGGCyaSTxAA out.pub (ED25519)
```

## Usage

```
$ ed25519brute -authorized-key-suffix test
2024/03/20 20:37:56 start
2024/03/20 20:38:05 found
% cat out.pub
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAINynu9CvEi6Yav1Y2L7hNxtD63RiHZkOG/ZsVzsNtest
```
```
% ed25519brute -fingerprint-prefix hello
2024/03/20 20:39:54 start
2024/03/20 21:22:53 found
% ssh-keygen -l -f out
256 SHA256:helloz8d+urX+JvZmOVdewcWAx89vXeoKTLsUH0mgBc out.pub (ED25519)
```
```
$ ed25519brute -fingerprint-suffix KEY
2024/03/20 21:23:11 start
2024/03/20 21:23:11 found
% ssh-keygen -l -f out
256 SHA256:8qN1j+/pE1VFyPzIzi6S9Njqvwtw52PIQJqCj9K8KEY out.pub (ED25519)
```

## A Small CTF Challenge

This is a joke software, but there was a serious bug in commit `7db96da05684a86bdbea18319ecc39097d0320d4`.

Can you recover the private key generated by the following command? Of course, it can be recovered in about an hour.

```
% git rev-parse HEAD
7db96da05684a86bdbea18319ecc39097d0320d4
% go run ./main.go -authorized-key-suffix a
2024/03/25 23:51:08 start
2024/03/25 23:51:08 found
% cat out.pub
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIBVji5kBXa8PbDP1nk+nysVA89VMg27z98D4aVT/j4Fa
```
