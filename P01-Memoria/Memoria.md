# Projecte de Modernització IT – FoodLogístic S.A.

## Introducció

FoodLogístic S.A. és una empresa de logística alimentària amb seu a Mataró que ha experimentat un creixement notable en volum de dades, nombre d’usuaris i necessitats de comunicació interna i externa.  
Aquest creixement ha posat de manifest les limitacions de la seva infraestructura actual, especialment pel que fa a la **seguretat**, la **disponibilitat dels serveis** i la **continuïtat del negoci**.

L’objectiu d’aquest projecte és presentar una **proposta tècnica integral** que permeti a FoodLogístic S.A.:

- Escalar la seva infraestructura de manera segura.
- Garantir la disponibilitat dels serveis crítics.
- Modernitzar els sistemes de comunicació i col·laboració.
- Complir amb la normativa legal i de protecció de dades.
- Millorar la seva presència digital.

La solució es planteja amb un enfocament **realista, professional i alineat amb les necessitats reals del client**, seguint bones pràctiques del sector TIC.

---

## Anàlisi de necessitats

### Context del sector i competència (T01)

S’ha realitzat un estudi del sector TIC i de la competència local per entendre el context en què opera el client com a consumidor de serveis tecnològics.

Empreses analitzades:
- **Digitalnet**
- **DYD Serveis Informàtics**
- **Alphanet Solutions**

| Empresa | Serveis principals | Mida aproximada |
|------|------------------|----------------|
| Digitalnet | Infraestructura, suport, cloud | Mitjana |
| DYD Serveis Informàtics | Xarxes, manteniment, servidors | Petita |
| Alphanet Solutions | Cloud, ciberseguretat, consultoria | Mitjana |

L’anàlisi mostra que el valor diferencial ha de basar-se en:
- Tracte proper i de confiança.
- Solucions ben documentades.
- Especial atenció a la seguretat i la continuïtat del negoci.

També s’ha elaborat una **radiografia dels departaments TIC típics**, identificant recursos humans necessaris (sistemes, suport, seguretat), fet que permet dimensionar adequadament la proposta.

---

## Proposta de solució

La proposta cobreix les **quatre àrees clau** sol·licitades pel client:

1. Infraestructura local amb alta disponibilitat.
2. Correu i eines de col·laboració al núvol.
3. Seguretat i formació en LOPD.
4. Presència web corporativa i compliment legal.

Les solucions es dissenyen de manera integrada, evitant sistemes aïllats i facilitant la gestió futura.

---

## Infraestructura i alta disponibilitat

### Servidor de fitxers (T03)

S’ha implementat un servidor de fitxers basat en **Active Directory**, orientat al treball diari amb documentació logística (albarans, informes i documents interns).

**Característiques principals:**
- Organització d’usuaris mitjançant **OU per departaments**.
- Control d’accés amb **grups de seguretat**.
- Carpetes compartides amb permisos **SMB i NTFS**.
- **Access-Based Enumeration** per ocultar carpetes no autoritzades.
- Gestió d’espai amb **quotes NTFS** i **FSRM**.
- Bloqueig de tipus de fitxers no permesos (executables i multimèdia).

| Carpeta | Accés | Mesures destacades |
|------|------|----------------|
| Public | Tothom | Permisos controlats |
| Operacions | Transport | ABE + filtres |
| Direcció | Direcció | GPO + unitat mapada |

*Captures incloses: estructura de l’AD, permisos NTFS, configuració de quotes.*  
img/t03-fitxers.png

---

### Servidor d’impressió (T04)

Per garantir una impressió fiable al magatzem, s’ha desplegat un servidor d’impressió amb **alta disponibilitat lògica**.

**Solució aplicada:**
- Rol **Print and Document Services**.
- Dues impressores amb **printer pooling**.
- Desplegament automàtic mitjançant **GPO**.
- Restriccions horàries d’ús.
- Proves de càrrega amb múltiples documents simultanis.

**Flux d’impressió:**
Usuari → GPO → Cua virtual → Impressora disponible

img/t04-impressio-flux.png

---

## Serveis al núvol

### Correu i col·laboració (T07)

S’han comparat diverses plataformes de correu al núvol, tenint en compte preu, funcionalitats i adopció al mercat.

**Solució escollida:**  
✅ **Microsoft 365 Empresa Estàndard**

**Justificació:**
- Correu professional amb Exchange Online.
- Eines col·laboratives (Teams, OneDrive i SharePoint).
- Alta disponibilitat i seguretat integrada.
- Plataforma àmpliament coneguda pels usuaris.

| Concepte | Valor |
|-------|------|
| Usuaris | 35 |
| Cost anual | **4.536 € / any** |

---

## Seguretat i LOPD

### Formació en protecció de dades (T05)

La seguretat no és només tecnològica, sinó també humana.  
Per aquest motiu, s’ha creat un **vídeo formatiu curt** destinat a tota la plantilla.

**Contingut del vídeo:**
- Què són les dades personals.
- Bones pràctiques diàries.
- Bloqueig de sessió i contrasenyes segures.
- Riscos de pendrives i núvols personals.
- Impressió segura.
- Destrucció de documents.
- Referències a normativa oficial.

🡒 *Enllaç al vídeo inclòs al repositori.*  
img/t05-video.png

---

### Web legal i compliment normatiu (T06)

S’ha adaptat la web corporativa per complir amb la **LOPD i la LSSI**, mantenint el disseny original.

**Mesures aplicades:**
- Avís legal.
- Política de privacitat.
- Política de cookies.
- Banner de cookies.
- Formulari de contacte amb consentiment explícit.

🔗 Web: https://pau-guerrero.github.io/web-corporativa2/  
🔗 Repositori: https://github.com/Pau-Guerrero/web-corporativa2

img/t06-web-legal.png

---

## Presència web

### Web corporativa base i tria final (T02 i T08)

Inicialment s’ha desenvolupat una **web corporativa base** (T02).  
Posteriorment, s’han comparat les propostes de Pau i Vicenç (T08).

| Criteri | Pau | Vicenç |
|-------|----|------|
| Disseny | Molt clar | Correcte |
| Estructura | Senzilla | Més carregada |
| Llegibilitat | Alta | Mitjana |

✅ **Decisió final:** combinació de les dues propostes, prioritzant claredat, estructura i compliment legal.

---

## Arquitectura i disseny tècnic

La solució segueix una arquitectura híbrida:

- Infraestructura local per a fitxers i impressió.
- Serveis al núvol per a comunicació i col·laboració.
- Seguretat reforçada amb polítiques i formació.

img/arquitectura-general.png

---

## Planificació

La planificació del projecte s’ha fet tenint en compte:
- Equip de **2 persones (Pau i Vicenç)**.
- Treball exclusiu entre setmana.
- Dependències reals entre tasques.

**Hores totals:** **78,5 hores**

**Camí crític:**  
`T01 → T02 → T06 → T08`

img/t09-gantt.png

---

## Pressupost (T10)

### Costos d’implantació (únics)

| Concepte | Cost |
|-------|------|
| Infraestructura i configuració | XXX € |
| Hores de treball | XXX € |
| Llicències inicials | XXX € |

### Costos recurrents

| Servei | Cost |
|-------|------|
| Microsoft 365 | 4.536 € / any |
| Hosting i domini | XXX € / any |
| Suport i manteniment | XXX € / mes |

El preu/hora es calcula segons tarifes de mercat en serveis TIC professionals, justificant qualitat, suport i continuïtat del servei.

---

## Conclusions

La proposta presentada permet a FoodLogístic S.A.:

- Disposar d’una infraestructura escalable i segura.
- Garantir la disponibilitat dels serveis crítics.
- Modernitzar la comunicació interna.
- Complir amb la normativa legal i de protecció de dades.
- Millorar la seva imatge corporativa i presència digital.

Es tracta d’una solució **realista, ben documentada i alineada amb el creixement de l’empresa**, preparada per ser implantada amb garanties.

---

**Autors:**  
Pau i Vicenç  