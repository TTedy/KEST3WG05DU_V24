1. **Stilla upp þjóninn með síðustu IPv4 tölustaf í fyrsta netið 192.168.100.0/25, Athugið að þú þarft að stilla réttu netkortið.**

   - Opnaðu stjórnborðið og farðu í Network Connections.
   - Finndu netkortið sem tengist netinu 192.168.100.0/25.
   - Opnaðu eigindin á netkortinu og stilltu IPv4 stillingar.
   - Settu síðustu IPv4 tölustafina í reitina og stilltu netmaskann rétt (255.255.255.128).

   ![ip addressa](/myndir/ip.png)
   ![ip addressa](/myndir/ip2.png)

2. **Breyttu nafni þjónsins í dc01.**

   - Opnaðu System Properties með því að hægri-smella á This PC og velja Properties.
   - Velja Change settings undir Computer name, domain, and workgroup settings.
   - Í Computer Name fananum, velja Change og slá inn nýja nafnið (dc01).

3. **Settu upp AD DS þjónustu- og stillið hana sem DC (Domain Controller) í nýrri skógi og notaðu ddp-yourname.local sem lén.**

   - Keyra upp Server Manager og velja Add roles and features.
   - Velja Active Directory Domain Services og fylgja leiðbeiningunum til að setja þjónustuna upp.
   - Eftir að þjónustan er sett upp, opnaðu Active Directory Domain and Trusts og búðu til nýjan skóga með ddp-yourname.local léninu.

    ![domina](/myndir/ip2.png)

4. **Settu upp og stilltu DHCP þjónustu með IPv4 svæði, nefndu það Client_Scope, og útilokaðu síðustu 10 tölurnar úr svæðinu.**

   - Keyra upp Server Manager og velja Add roles and features.
   - Velja DHCP Server og fylgja leiðbeiningunum til að setja þjónustuna upp.
   - Eftir að þjónustan er sett upp, stilltu upp svæðið og útilokaðu síðustu 10 tölurnar í svæðinu.

    ![dchp](/myndir/Dhcp.png)
5. **DHCP þarf að úthluta IP-tölu, sjálfgefna gátt og lén til viðskiptavina í netinu.**

   - Inn á DHCP Manager í Server Manager, stilltu upp svæðið sem þú búðir til og stilltu sjálfgefnu gáttinn og DNS lén.

6. **Vissu þig um að Windows 10 fái sjálfgefna IP-tölu með DHCP og að tengjast Windows 10 við skráarsafnið.**

   - Á Windows 10 tölvunni, stilltu netkortið á DHCP.
   - Notaðu Run promptið (Windows + R) til að opna "sysdm.cpl" og tengdu Windows 10 við skráarsafnið með því að fylgja leiðbeiningunum.

7. **Búðu til NAT á þjóninum svo að Windows viðskiptavinir fái aðgang að interneti með einkareitnum.**

   - Keyra upp Server Manager og velja Add roles and features.
   - Velja Routing and Remote Access þjónustuna og fylgja leiðbeiningunum til að setja þjónustuna upp og stilla upp NAT.

    ![NAT](/myndir/nat%20server.png)
8. **Búðu til OU (Organizational Units) fyrir hvert deild.**

   - Inn á Active Directory Users and Computers, hægri-smella á Domain og velja New > Organizational Unit.

9. **Búðu til hópa og viðkomandi notendur í hverjum hópi, notaðu `2024P@ssword` sem lykilorð fyrir alla notendur.**

   - Inn á Active Directory Users and Computers, hægri-smella á OU sem þú vilt búa hópinn í og velja New > Group.
   - Búðu til hópinn og bættu notendum við hópinn. Hægri-smelltu á hópinn, veldu Add Members og bættu við notendum.
   - Stilltu lykilorðið fyrir notendur sem `2024P@ssword`.

    ![notendur](/myndir/11%20it%20group%20remote.png)
10. **Bættu við notendum í OU stjórnunarflokknum í Domain Administrators hópinn.**

    - Hægri-smelltu á OU stjórnunarflokksins og veldu Add Member.
    - Bættu við notendum sem þú vilt hafa aðgang að Domain Administrators hópnum.

11. **Bættu IT hópnum við Remote Desktop Users í Active Directory.**

    - Inn á Active Directory Users and Computers, hægri-smelltu á IT hópinn og velja Properties.
    - Farðu í Member Of flipann og hægri-smelltu á Remote Desktop Users hópinn og veldu Add.

    ![notendur](/myndir/11%20it%20group%20remote.png)
12. **Búðu til sameignarvalmynd fyrir hvern hóp á C-disknum, notendur í IT ættu að hafa fullan aðgang að öllum möppum en öðrum hópum ætti aðeins að hafa aðgang að eigin sameignarmöppum.**

    - Búa til möppu á C-disknum fyrir hvern hóp og stilltu aðgangstillögur þannig að IT hópurinn hafi fullan aðgang en aðrir hópar aðeins aðgang að eigin möppum.
    ![permissions](/myndir/Folder%20permissions.png)