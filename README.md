#### Recuperação da Partição de Boot (System) UEFI/GPT

>[!IMPORTANT]
>Iniciar o computador com pendrive de instalação do windows.
>
> Reparar o computador --> Solução de Problemas --> Prompt de Comando

```
diskpart
```
```
list disk
```
>[!NOTE]
>Selecione o disco onde o windows está instalado
>
> ```select disk 0```


>[!IMPORTANT]
>Anote a nova letra da partição C:
>
> ``` detail disk ```

```
list partition
```

>[!NOTE]
>Selecione a partição EFI
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

>[!IMPORTANT]
>Selecione o volume da partição System
>
```
select volume "x"
```

```
remove letter S
```

