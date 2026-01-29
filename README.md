# Workshop: Git Flow

I denna workshop kommer ni att arbeta steg‑för‑steg för att träna på att använda **Git Flow** i grupp. Syftet är att öva på:

* att arbeta med flera brancher
* att skapa och använda pull requests
* att hantera merge‑konflikter
* att samarbeta på ett kontrollerat och säkert sätt

Använd **Git Bash** när ni arbetar lokalt.

---

## Steg 1 – Skapa repository

1. Välj ut **en person i gruppen** som skapar ett nytt GitHub‑repo.

   * Repo:t kan vara privat eller publikt.
2. Lägg till alla övriga gruppmedlemmar som **collaborators** så att alla har rätt att pusha och skapa pull requests.

---

## Steg 2 – Skapa `dev`‑branch

1. Alla i gruppen klonar repo:t lokalt:

   ```bash
   git clone <repo-url>
   ```

2. Alla i gruppen skapar er lokala `dev`‑branch:

   ```bash
   git branch dev
   git checkout dev
   ```

3. En person i gruppen pushar `dev` till Github:

   ```bash
   git push origin dev
   ```

Nu arbetar alla vidare från `dev`.

---

## Steg 3 – Branch Protection Rules

För att skydda projektet ska ni skapa branch‑regler.

### Regel 1 – Skydda `main`

1. Gå till **Settings → Rules → Rulesets**.
2. Klicka på **New branch ruleset**.
3. Namn: `Main protection rule`
4. Enforcement status: **Active**
5. Target branches → **Include by pattern** → `main`
6. Under *Branch rules*:

   * Bocka i **Require a pull request before merging**
   * Sätt **Required approvals** till *antal personer i gruppen minus 1*
7. Klicka på **Create**.

---

### Regel 2 – Skydda alla andra brancher

1. Skapa ytterligare en ruleset.
2. Namn: `Branch protection`
3. Enforcement status: **Active**
4. Target branches → **Include all branches**
5. Under *Required approvals*: sätt värdet till **1**
6. Klicka på **Create**.

---

## Steg 4 – Ändra default‑branch (valfritt)

För att undvika att pull requests av misstag skapas mot `main` kan ni ändra default‑branch:

1. Gå till **Settings → General**
2. Hitta **Default branch**
3. Byt från `main` till `dev`

---

## Steg 5 – Arbeta med tasks

Ni hittar alla tasks i filen [tasks.md](./tasks.md).

Gör klart **5a innan ni går vidare till 5b**, osv.

Efter varje pull request så raderar ni den genomförda `feature`-branchen, både på Github och lokalt.
För att radera en lokal branch måste du först hoppa över till en annan branch, förslagsvis `dev`. Skriv därefter:

```bash
git branch -D <namn-på er-branch>
```

---

### 5a – Feature‑brancher utan konflikter

1. Plocka **en task per person** tills task 1–6 är klara.
2. Skapa en feature‑branch lokalt:

   ```bash
   git branch <namn-på-er-branch>
   git checkout <namn-på-er-branch>
   ```
3. Lägg in koden för er task.
4. Stagea och committa (gärna i flera steg):

   ```bash
   git add .
   git commit -m "<beskrivning>"
   ```
5. Pusha er branch:

   ```bash
   git push origin <namn-på-er-branch>
   ```
6. Skapa en **pull request till `dev`** och låt en lagkamrat reviewa.

---

### 5b – Konflikter online (GitHub)

1. Plocka tasks 7–12, en per person.
2. Arbeta på samma sätt som i 5a **men skapa inga pull requests direkt**.
3. När **alla** är klara med sina tasks:

   * Börja skapa pull requests till `dev`
   * Lös konflikterna **direkt i GitHub**

Kommunicera med varandra innan ni mergar.

---

### 5c – Lösa konflikter lokalt

I detta steg fortsätter ni med task 13-17, men nu ska konflikter istället **lösas lokalt på er dator**.
För att övningen skall fungera så är det viktigt att ni enbart uppdaterar er egen `dev`-branch **INNAN** ni sätter igång. Normalt så vill vi göra det varje gång innan vi skapar en ny `feature`-branch, men för att medvetet orsaka konflikter så är det viktigt att ni **inte** gör det i 5c.

⚠️ Följ stegen i exakt ordning.

#### Innan ni börjar

1. Byt till `dev`:

   ```bash
   git checkout dev
   ```
2. Hämta senaste versionen:

   ```bash
   git pull origin dev
   ```

Detta är alltså den enda gången i övening 5c som ni gör en pull till er lokala `dev`-branch.

---

#### Arbetsgång

1. Skapa er feature‑branch:

   ```bash
   git branch <namn-på-er-branch>
   git checkout <namn-på-er-branch>
   ```

2. Lägg in koden för er task och spara.

3. Stagea och committa:

   ```bash
   git add .
   git commit -m "Lägger till <task>"
   ```

4. Hämta senaste ändringarna från `dev`:

   ```bash
   git pull origin dev
   ```

👉 Här **ska konflikter uppstå**.

5. Lös konflikterna genom att:

   * läsa konfliktmarkeringarna
   * prata med era lagkamrater
   * kolla så att koden stämmer

6. Stagea, committa och pusha igen:

   ```bash
   git add .
   git commit -m "Löser merge-konflikter"
   git push origin <namn-på-er-branch>
   ```

7. Skapa en pull request till `dev` och merga efter godkännande.

---

### 5d – Extra tasks

Lägg nu även in task **18–20** enligt korrekt arbetssätt.

---

## Steg 6 – Slå ihop `dev` till `main`

1. Skapa en pull request från `dev` till `main`.
2. Assigna övriga i gruppen som **reviewers**.
3. När alla godkänt: **merga till `main`**.

🎉 Workshop klar!
