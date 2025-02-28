#### Recuperação da Partição de Boot (System) UEFI/GPT

```
diskpart
```
```
list disk
```
```
select disk 0
```
>[!IMPORTANT]
>Anote a nova letra da partição C:
>
> ``` detail disk ```

```
list partition
```
```
select partition 1
```
```
format quick fs=fat32 label="System"
```
```
assign letter="S"
```
```
detail disk
```
```
exit
```
###### Partiação EFI (UEFI e BIOS Legacy)

```
bcdboot D:\Windows /s S:/f ALL
```

###### Particão EFI (UEFI)

```
bdcboot D:\Windows /s S:/f UEFI
```
##### Remover letra da partição EFI (Opcional)

```
diskpart
```
```
list volume
```
```
select volume "x"
```
```
remove letter S
```

