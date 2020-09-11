# Fra disk til filer

## Uden LVM

1. Disk
1. (Hardware-RAID)
1. (Parttition)
1. (Software-RAID)
1. Filsystem
1. Fil





## Med LVM

1. Disk
1. (Hardware-RAID)
1. (Parttition)
1. (Software-RAID)
1. LVM
    1. pv - Fysisk volume
    1. vg - Voloume group
    1. lv - Logisk volume
1. Filsystem
1. Fil





## Disk

1. Disk

Typisk en harddisk eller SSD koblet på via SATA eller USB, men der er mange andre muligheder

1. (Hardware-RAID)
1. (Parttition)
1. (Software-RAID)
1. Filsystem
1. Fil





## Hardware-RAID

1. Disk
1. (Hardware-RAID)

Indbygget controler som på hardware-niveau kobler diske sammen, så de for OS'et fremstår som en enkelt disk.

**RAID0** Striping - ingen sikkerhed ved død disk\
**RAID1** Mirroring - alle diske inderholder alle data\
**RAID5** Parity med 1 disk - en død disk kan genopbygges\
**RAID6** Parity med 2 diske - to døde diske kan genopbygges\

Kombinationer af overstående

1. (Parttition)
1. (Software-RAID)
1. Filsystem
1. Fil





## Partition

1. Disk
1. (Hardware-RAID)
1. (Parttition)

Opdeling af en disk i mindre bidder. Der tildeles en vis mængde diskplads til en opgave.

**Fordelen** at en fyldt disk ikke slår hele maskine ihjel.

**Ulempen** er at pladsen er relativt fast.

1. (Software-RAID)
1. Filsystem
1. Fil





## Software-RAID

1. Disk
1. (Hardware-RAID)
1. (Parttition)
1. (Software-RAID)

Software som udfører samme funktion som hardware-RAID, men da det er ren software kan det også køre på partitioner.

1. Filsystem  
1. Fil





## Hardware- vs software-RAID

Dør din RAID-controler er dine data tabt.

Det kan på nogle controlere være svært at hente SMART-data ud af de fysiske diske så man kan holde øje med helbreds-tilstanden.

Da arbejdet ved hardward-RAID ikke udføres af cpuen, belaster det ikke maskinen.





## Filsystem

1. Disk
1. (Hardware-RAID)
1. (Parttition)
1. (Software-RAID)
1. Filsystem

**Ext{2,3,4}** er traditionelt det brugte filesystem på linux. ext3 fik journalisering, ext4 bedre håndtering af pladsen.

**FAT** er egentligt et skod-fs der ikke er særligt robust. Derfor HUSK at unmounte det inden du fjerner din USB-stick.

**NTFS** bruges af windows.

**ZFS** og et utal af andre.

1. Fil





## Fil

1. Disk
1. (Hardware-RAID)
1. (Parttition)
1. (Software-RAID)
1. Filsystem
1. Fil

Her ligger dine data i alle dine filer.





## LVM - pv - Fysisk volume

1. Disk
1. (Hardware-RAID)
1. (Parttition)
1. (Software-RAID)
1. LVM
    1. pv - Fysisk volume

En klump diskplads som man ønsker at bruge. Typisk en hel disk eller en partition.

    1. vg - Voloume group
    1. lv - Logisk volume
1. Filsystem
1. Fil





## LVM - vg - Voloume group

1. Disk
1. (Hardware-RAID)
1. (Parttition)
1. (Software-RAID)
1. LVM
    1. pv - Fysisk volume
    1. vg - Voloume group

En samling af klumper diskplads som man ønsker at bruge sammen

    1. lv - Logisk volume
1. Filsystem
1. Fil





## LVM - lv - Logisk volume

1. Disk
1. (Hardware-RAID)
1. (Parttition)
1. (Software-RAID)
1. LVM
    1. pv - Fysisk volume
    1. vg - Voloume group
    1. lv - Logisk volume

Et stykke diskplads ønsker at bruge til data.

Hvis der er behov for det kan stykkerne flyttes til eller fra en en specik disk.
Enten fordi den disk er hurtigere, eller fordi den er begyndt at vis svaghedstegn.

1. Filsystem
1. Fil





## LVM

Mulighed for at indsætte en lynhurtig disk som cache for de langsomme. 

Allokere disk-plads på en konroleret måde, uden at alt give adgang til al pladsen.

Let at allokere et stykke disk-plads til midlertidig brug. Den kan bare slettes igen, og er automatisk klar til brug igen i vg'en.

Efter sigende meget lille performance-tab.

Husk at holde øje med plads-forbruget i dine lv'er.

En disk død, og dine data er tabt - **husk backup**.
