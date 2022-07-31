---
title: MeetPlan aplikacija za računalnike
---

{{< toc >}}

MeetPlan ima tudi aplikacijo za računalnike, zgrajeno s [Taurijem](https://tauri.app/), kar pomeni, da je to v resnici samo spletna aplikacija zapakirana v izvršilne datoteke.

![image](https://user-images.githubusercontent.com/52399966/167269792-e58dfa23-33c9-4b82-bd50-9c26b57328ac.png)
*MeetPlan aplikacija na Fedori 36*

## Prenos
{{< button href="https://github.com/MeetPlan/MeetPlanFrontend/releases/latest" >}}Prenos - Windows, Linux, MacOS{{< /button >}}

***Android in iOS aplikaciji še prihajata.***

## Pogosta vprašanja in odgovori
### Kakšen je URL do MeetPlan sistema, katerega zahteva aplikacija ob prijavi?
Če vaša šola uporablja [MeetPlanDocker](https://github.com/MeetPlan/MeetPlanDocker), kar je najbolj verjetno, je URL katerega morate vtipkati, naslednji:
```
URL do spletne verzije aplikacije + /api
```
Na primer, če je moja spletna aplikacija na naslovu https://demo.meetplan.si, je moj zahtevan URL https://demo.meetplan.si/api.

### Kako je aplikacija čisto enaka spletni aplikaciji?
Uporabljamo [Tauri](https://tauri.app/), kar je podobno kot [Electron](https://www.electronjs.org/). Predstavljajte si to tako, kot da bi poganjali spletno aplikacijo, samo da je ta zapakirana v posebej namenjeni aplikaciji.

### Aplikacija javlja napake samo pri specifičnih funkcijah.
Če te funkcije ***NI*** na spletni aplikaciji, pomeni to, da vaša aplikacija uporablja verzijo, novejšo od samega strežnika, kar pomeni da hoče aplikacija neke podatke, ampak strežnik sploh še nima vgrajene te funkcije. To je ena izmed naših prioritet popraviti.
