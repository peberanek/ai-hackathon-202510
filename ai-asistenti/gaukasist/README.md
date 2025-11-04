# GAUKasist

## Autoři

- realizace: Mgr. Dominik Starý, model GPT-5-Chat
- technická pomoc: Pavel Sklenář (společnost CloudField)

## Jaký problém jsme se snažili vyřešit

- Cílem bylo navrhnout asistenta, který by byl schopen radit žadateli a GAUK. Zejména pro studenta, který žádá o takovýto grant poprvé, může být složité zorientovat se ve všech kritériích.
- GAUKasist má za úkol:
    - Umět sdělit deadline aktuálního ročníku a kontaktní údaje na odpovědnou osobu
    - Kontrolovat plnění kritérií u vkládaného textu
    - Navrhovat doporučení v roli oponenta
    - Navrhovat rozpočet (včetně pracovních cest)
    - Kontrolovat věcný obsah v roli vedoucího

## Co jsme se naučili

Např.: Co se povedlo? Co se nepovedlo? S jakými problémy jste se potýkali? Možné budoucí změny a vylepšení.

- gpt-oss-120b v návrhu změnil původně anglický text na český
- gpt-5-chat jednou navrhnul doporučení pro úpravu rozpočtu, ale zapomněl na jiné kritérium

## Doplňující poznámky

Např.: Konfigurační a instalační instrukce, které nejsou zřejmé z exportovaného konfiguračního souboru.

- Z nástrojů byl použit Web Search a ArXiv Search Tool.
- Jako knowledge base slouží nahrané dokumenty UKEN-756-version1-information_for_submitting_new_project_proposals a UKEN-756-version1-information_on_submitting_the_pdf___project_proposal, kde je seznam kritérií.
- GAUKasist je zaměřený na studenta MFF UK, takže informace o deadlinech a kontaktech bere z https://www.mff.cuni.cz/cs/ogap/gauk
- Znalosti pro pracovní cesty jsou omezené na Flixbus a přednastavenou částku za noc
