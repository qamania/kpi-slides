# Quality Engineering у 2030 році: від тестування ПЗ до інженерії довіри в AI-опосередкованому SDLC

## Головний висновок

Станом на **20 серпня 2026 року** твоє розділення на **QE with AI** та **QE for AI** дуже добре описує першу фазу трансформації професії. Але, на мою думку, воно вже починає ставати недостатнім.

Найважливіший висновок цього дослідження такий:

> **До 2030 року головна межа проходитиме не між “QE, який користується AI” і “QE, який тестує AI”. Вона проходитиме між QE, який виконує тестову роботу, та QE, який проєктує систему доказів того, що складна software+AI система є достатньо якісною, безпечною і контрольованою для певного бізнес-ризику.**

Тобто я вважаю твою гіпотезу про злиття **QE with AI + QE for AI** переважно правильною. Але до цих двох гілок додається третя, яка зрештою і поглинає їх обидві:

**QE over AI-mediated SDLC** — умовна назва для Quality Engineering над усією системою виробництва ПЗ, де код, тести, документацію, аналіз дефектів, частину архітектурних рішень і навіть саму валідацію дедалі частіше виконують AI-агенти.

Схематично еволюція виглядає так:

> **QA:** “Чи є в готовому продукті дефекти?”  
> ↓  
> **QE:** “Як інженерно не допустити дефектів у всьому SDLC?”  
> ↓  
> **AI-augmented QE:** “Яку частину цієї роботи може виконувати AI?”  
> ↓  
> **AI Quality Engineering:** “Як перевірити систему, поведінка якої частково генерується AI?”  
> ↓  
> **Continuous Assurance:** “Як постійно отримувати достатні докази, що human+software+AI+agents система залишається прийнятною за якістю та ризиком?”

Це не просто зміна інструментів. Це зміна **об'єкта роботи QE**.

До AI найдорожчим ресурсом часто було **створення тестів і виконання тестування**. Коли AI різко здешевлює генерацію тест-кейсів, automation-коду, test data та аналіз результатів, дефіцитним ресурсом стає зовсім інше: **знати, що саме треба перевірити, як сформулювати правильний oracle, які ризики є суттєвими, які результати можна вважати достатніми доказами і коли системі можна довіряти**. Це добре узгоджується і з поточним рухом AI-інструментів у QE, і з практиками оцінювання AI-агентів, де центральними стають eval cases, graders, traces, production monitoring та human calibration. citeturn20search0turn21search0turn21search1

І важливо: наявні дані **не підтримують просту тезу “AI прибере тестувальників”**. Американський BLS все ще прогнозує зростання зайнятості Software QA Analysts and Testers на **10% між 2024 і 2034 роками**, хоча це американська статистика і категорії BLS неминуче відстають від зміни фактичних ролей. Водночас World Economic Forum оцінює, що до 2030 року приблизно **39% наявних skills працівників зміняться або застаріють**, причому AI/big data є найшвидше зростаючою групою навичок, а analytical thinking залишається найважливішою core skill. Отже, найбільш імовірна картина — **не зникнення QE, а дуже сильне знищення одних QE-задач і зростання інших**. citeturn18search0turn18search8turn18search1

Мої суб'єктивні сценарні оцінки на 2030 рік такі:

| Сценарій | Моя оцінка ймовірності | Що стається з QE |
|---|---:|---|
| **Converged Quality / Trust Engineering** | **55%** | QE with AI та QE for AI значною мірою зливаються; QE керує quality gates, evals, agents, observability, risk та evidence |
| **Дві професійні гілки співіснують довше** | **30%** | звичайний QE переважно використовує AI, а AI-first продукти мають окремих AI Evaluation / AI Assurance спеціалістів |
| **Autonomous SDLC compression** | **15%** | coding/testing agents забирають більшість execution-level роботи; QE-команди стають меншими, але значно більш senior і risk-oriented |

Ці відсотки — **не статистичний прогноз**, а моя сценарна оцінка на основі стану технологій, adoption, ринку праці, стандартів і регуляції станом на серпень 2026 року. Важливо, що навіть найагресивніший сценарій не означає “quality більше не потрібна”. Навпаки: чим більше software-producing autonomy отримують агенти, тим більше виникає потреба у незалежних механізмах validation, monitoring, governance та rollback. DORA у 2024 році вже спостерігала характерний ефект: AI покращував індивідуальну productivity/flow, але це не автоматично покращувало delivery — у дослідженні одночасно погіршувалися stability та throughput. У 2025 році DORA сформулювала ще сильніший висновок: AI насамперед працює як **amplifier**, посилюючи як хороші, так і погані властивості інженерної системи організації. citeturn22search0turn22search1

## Як професія QE дійшла до точки біфуркації 2023 року

Історію software testing корисніше дивитися не як історію інструментів, а як історію **розширення відповідальності за якість**.

| Період | Основне запитання до якості | Домінантна роль QE/QA | Головний зсув |
|---|---|---|---|
| 1980-ті–1990-ті | “Чи відповідає продукт процесу та специфікації?” | QA як окрема контрольна функція | від ad-hoc testing до керованого quality process |
| 2000-ті | “Як знайти проблему раніше?” | tester всередині development lifecycle | Agile, shift-left, рання участь QA |
| 2010-ті | “Як забезпечувати якість при постійному delivery?” | automation/SDET/QE | CI/CD, continuous testing, DevOps |
| 2010-ті–2022 | “Як знати, що система працює в production?” | QE + SRE + observability | shift-right, telemetry, resilience |
| 2015–2022 паралельно | “Як тестувати систему, поведінка якої залежить від data/model?” | ML testing / ML reliability | data validation, model validation, drift, monitoring |
| 2023+ | “Як контролювати ПЗ, яке і створюється AI, і містить AI?” | AI-augmented QE → AI Quality Engineering | agentic automation + probabilistic assurance |

У 1980-х і 1990-х quality дедалі більше інституціоналізувалася як **процес**, а не лише заключна перевірка продукту. Наприклад, Software Engineering Institute почав розробляти process-maturity framework у 1986 році, а в 1991 році опублікував Software Capability Maturity Model; SEI описує його як модель, що дала організаціям об'єктивний орієнтир для software process improvement і суттєво вплинула на сприйняття software quality у державному секторі та індустрії. citeturn17search3turn17search9

Наступна фундаментальна зміна сталася з Agile. Принципи Agile Manifesto поставили в центр раннє й регулярне постачання working software, частий delivery, тісну взаємодію між бізнесом і developers та постійну увагу до technical excellence. Це неминуче руйнувало модель, у якій QA існує лише як окрема заключна фаза. citeturn17search1

Того ж історичного періоду походить і сам термін **shift-left testing**. Larry Smith у 2001 році описував його саме як інтеграцію QA та development і залучення QA якомога раніше, замість додавання testability наприкінці. citeturn9search0

У 2010-х automation перестала бути лише “написанням Selenium tests”. Якість потрапила в CI/CD pipeline, а feedback loop почав вимірюватися хвилинами. Наприклад, дослідження Google's continuous integration infrastructure описувало pre-submit і post-submit test selection/prioritization саме для того, щоб підтримувати швидкий feedback при величезному обсязі regression tests. citeturn9search12

Одночасно виник протилежний рух — **shift right**. Google SRE прямо розглядає testing як механізм отримання confidence у reliability системи, але підкреслює, що staging ніколи повністю не відтворює production, тому staged rollouts, monitoring і production testing залишаються необхідними. Це важлива історична зміна: quality перестає закінчуватися на release. citeturn9search2turn9search6

Таким чином, задовго до LLM професія вже рухалася:

**від inspection → до prevention → до continuous feedback → до production assurance.**

Це критично для прогнозу на 2030 рік, тому що AI **не створив цей напрямок**. Він різко його прискорив.

Є ще одна надзвичайно важлива деталь: **QE for AI насправді не народився у 2023 році**.

Ще в 2015 році робота Google *Hidden Technical Debt in Machine Learning Systems* описувала специфічні для ML production systems проблеми: data dependencies, feedback loops, entanglement, external-world changes та системний technical debt. citeturn11search0

У 2017 році Google's *ML Test Score* вже стверджував, що production ML породжує проблеми, яких немає у звичайних offline experiments, що testing і monitoring є ключовими для production readiness, а конкретну prediction behavior часто складно повністю специфікувати наперед. Автори запропонували **28 конкретних tests та monitoring needs**. citeturn17search2

Паралельно production ML змусив quality discipline підняти **data** до рівня повноцінного test object: валідація, debugging, cleaning, understanding training data, detection of training-serving skew і monitoring змін у даних стали частиною reliability problem. citeturn17search11turn17search8

А у 2022 році Google Research прямо критикувала підхід, за якого testing ML model фактично зводився до predictive performance на held-out dataset, і пропонувала переносити до ML традиційні software-testing ідеї — corner cases та stress conditions. citeturn11search20

Тому **2023 краще називати не моментом народження AI Quality, а моментом, коли дві до того значною мірою паралельні історії почали зливатися**:

> mainstream software QE  
> **+**  
> ML/AI reliability  
> **→**  
> AI-native Quality Engineering.

Показово, що саме у 2023 році ISO опублікувала **ISO/IEC 25059:2023**, окрему SQuaRE quality model для AI systems. У 2025 році з'явилася **ISO/IEC TS 42119-2:2025**, присвячена безпосередньо testing AI systems. Тобто AI quality уже переходить від набору окремих engineering practices до формалізованої дисципліни. citeturn18search7turn18search6

Отже, до 2023 року вже сформувалися шість великих трендів, які AI тепер прискорює одночасно:

**quality earlier → quality continuously → automation → production observability → risk-based quality → data/model quality.**

Саме це, а не тільки поява LLM, є історичним фундаментом QE 2030.

## Що реально змінилося між 2023 і 2026 роками

Період 2023–2026 важливий не тим, що AI навчився генерувати test cases. Це було б лише ще одним поколінням automation.

Справжня зміна полягає в тому, що AI поступово переходить через три рівні:

> **Copilot:** “зроби мені цей artifact”  
> →  
> **Agent:** “виконай цю engineering task”  
> →  
> **Agentic workflow:** “досягни engineering outcome, сам обравши послідовність дій”.

І саме третій рівень змінює структуру професії.

DORA 2025 повідомляє, що **90% опитаних technology professionals уже використовували AI на роботі**; понад 80% суб'єктивно відчували productivity improvement, 65% повідомляли про щонайменше помірну залежність від AI tools, а 60% використовували їх приблизно в половині або більшій частині задач. При цьому DORA обережно формулює головний результат не як “AI робить усіх ефективнішими”, а як **AI is an amplifier**: результат дуже залежить від architecture, platform quality, version control, batch size, data ecosystem, user focus та інших характеристик engineering system. citeturn16view0turn22search1

У самому QE adoption уже теж вийшов далеко за межі PoC, але масштабування відбувається нерівномірно. World Quality Report 2025–26 повідомляє, що **43% опитаних організацій перебували на experimental stage GenAI у QA/QE, 30% — в operational use, але лише 15% масштабували його enterprise-wide**. Автори також спостерігали зміщення use cases від аналізу готових outputs — наприклад defect analysis — у бік **test-case design та requirements refinement**. citeturn20search0turn20search4

Це велика принципова зміна.

AI заходить у QE не тільки “знизу”, автоматизуючи execution, але й **“зліва” — у reasoning про те, що взагалі треба тестувати**.

У тому ж World Quality Report GenAI став top-ranked skill для QE серед респондентів — **63%**, але класичні core Quality Engineering skills майже не відстали — **60%**, а soft communication skills також залишилися високо в рейтингу. Водночас лише 15% enterprise-wide adoption показує, що ринок ще дуже далеко не пройшов повну трансформацію. Методологічно WQR варто читати саме як enterprise sentiment/practice survey: дослідження базувалося на **2 000 інтерв'ю із senior IT executives у 23 країнах**, а не на експериментальному вимірюванні individual QE productivity. citeturn20search3turn20search10

Інший цікавий сигнал: **productivity ≠ quality**.

DORA 2024 зафіксувала, що більша AI adoption корелювала з кращою individual productivity, flow та job satisfaction, але водночас із гіршими software delivery stability і throughput; дослідники наголошували на важливості robust testing та small batches. citeturn22search0

Навіть на рівні coding продуктивність AI виявилася дуже context-dependent. METR у randomized experiment з досвідченими open-source developers, які працювали у знайомих їм власних repositories, у першій половині 2025 року отримала парадоксальний результат: з AI tasks займали в середньому **на 19% більше часу**, хоча самі developers вважали, що AI їх пришвидшує. METR окремо застерігає від узагальнення цього результату на всю software engineering. citeturn22search2

До лютого 2026 року METR вже вважала дуже ймовірним, що нові AI tools пришвидшують цих developers більше, ніж ранні моделі 2025 року, але сам експеримент почав ламатися: частина developers відмовлялася брати участь, якщо могла отримати condition “без AI”, а використання кількох agents паралельно зробило task-duration значно гіршою метрикою. Тобто за один рік AI для частини developers перейшов із optional tool у **частину нормального способу роботи** настільки, що стало складно побудувати clean no-AI control group. citeturn22search3

Це важлива аналогія для QE: до 2030 року запитання **“чи використовує тестувальник AI?”** може звучати приблизно так само дивно, як сьогодні “чи використовує automation engineer IDE, Git або search engine?”.

Ще сильніша зміна — ріст agentic autonomy. METR вимірює так званий *task-completion time horizon*: складність задачі виражається часом, який вона займає у human expert, і вимірюється, на задачах якої довжини agent зберігає певну ймовірність успіху. Станом на травень 2026 року їхня suite вже охоплює понад сотню різноманітних software tasks, а frontier results вийшли у багатогодинний діапазон; METR прямо попереджає, що оцінки понад приблизно 16 годин наразі ненадійні через насичення benchmark suite. Саме обмеження benchmark вже є показовим сигналом про швидкість прогресу. citeturn23search0

Телеметрія Anthropic Claude Code дає ще один цікавий, хоча vendor-specific, зріз. У досліджених сесіях користувачі в середньому приймали приблизно **70% planning decisions**, але лише близько **20% execution decisions**: люди значною мірою визначали *що* робити і що вважати завершенням, тоді як agent частіше вирішував *як* це реалізувати. citeturn23search1

Це майже готовий прототип майбутньої ролі QE:

> Людина все менше визначає **кожен execution step**,  
> але все більше відповідає за **intent, constraints, acceptance criteria і verification**.

І agentic systems не роблять проблему quality простішою. Google Research у контрольованому експерименті з **180 конфігураціями agent systems** отримала дуже різну поведінку залежно від topology та типу задачі: multi-agent coordination дала приблизно +81% на одній паралелізованій задачі, але близько −70% на послідовній planning task. Центральний orchestrator також міг обмежувати propagation errors. Тобто вже сама **архітектура agent workflow стає quality variable, яку треба тестувати**. citeturn23search2

Звідси випливає величезна зміна в економіці QE.

Умовно:

**до AI**

> specification → людина пише tests → automation запускає tests → людина аналізує failure

**у 2026**

> specification → AI аналізує requirements → AI генерує tests → agent запускає/ремонтує automation → AI кластеризує failures → людина перевіряє результат

**біля 2030**

> business intent + risk constraints  
> → agents проєктують implementation і verification  
> → deterministic tests + probabilistic evals + simulations  
> → agents виконують SDLC  
> → automated quality gates  
> → production telemetry / online evals  
> → human QE втручається у high-risk, ambiguous або novel cases.

У цьому світі цінність QE зміщується **від production of test artifacts до design of the quality system**.

І тут виникає парадокс: що більше тестів AI може дешево генерувати, то менше сама кількість тестів говорить про quality.

Стає важливішим:

**Чому ці tests існують? Який risk вони покривають? Наскільки правильний oracle? Чого вони систематично не бачать? Чи незалежний evaluator від producer? Чи співпадає test distribution з production distribution?**

Це набагато ближче до engineering judgement, ніж до класичного “test-case authoring”.

## QE with AI та QE for AI — і чому вони справді починають зливатися

Твоя перша гілка, **QE with AI**, уже добре видима.

Найшвидше AI проникає саме в роботу, де є багато інформації та відносно добре сформульований output: аналіз requirements, генерація test ideas і test cases, створення synthetic test data, написання automation code, defect summarization, log analysis, maintenance та orchestration. World Quality Report 2025 прямо фіксує перехід GenAI use cases у QE від downstream analysis до test design та requirements refinement, а synthetic test data називає одним із ключових напрямів використання. citeturn20search3turn20search4

Але у міру переходу від copilot до agent змінюється сам характер automation.

Класичний automation framework автоматизує **відомий алгоритм**:

> click → enter → call → assert.

Agentic workflow автоматизує **частину вибору алгоритму**:

> зрозумій goal → досліди систему → виріши, які дії потрібні → виконай їх → оціни outcome → адаптуй strategy.

Саме тому AI-driven test agent уже не можна перевіряти тільки як звичайний automation script. Треба тестувати його **reasoning trajectory, tool choice, permissions, state, recovery behavior і side effects**.

І в цей момент **QE with AI стає QE for AI**.

У другій гілці, **QE for AI**, найбільша концептуальна помилка — думати, що test object = LLM.

Для production AI system правильніше мислити приблизно так:

> **AI system = model + system instructions + context + data/RAG + memory + tools + permissions + orchestration + external services + infrastructure + humans + monitoring.**

NIST AI Risk Management Framework for Generative AI спеціально розглядає trustworthiness на рівні design, development, use та evaluation протягом AI lifecycle, а не тільки benchmark score самої моделі. citeturn21search3

Сучасні agent evaluation frameworks рухаються в тому ж напрямку. Anthropic визначає eval як test для AI system, але для agentic system він уже може бути multi-turn, із tools, environment та state; рекомендується комбінувати automated evals, production monitoring і human review. citeturn21search0

Google's current agent-evaluation tooling оперує не лише final response. Eval case може включати conversation state і simulated user; execution створює **trace** з model inputs, responses і tool calls; окремо оцінюються task success, safety, tool use та trajectory, а evaluation можна проводити і на development test cases, і на production traces. citeturn21search1turn21search9

Це означає, що звичайні QE-концепти не зникають. Вони мутують:

| Класичний QE | AI-native аналог | Що принципово змінюється |
|---|---|---|
| Test case | Eval case / scenario | один сценарій часто треба запускати багато разів |
| Expected result | deterministic assertion / rubric / model judge / human judgement | правильна відповідь може бути множиною, а не одним value |
| Regression suite | Eval suite | regression може виникнути через model, prompt, retrieval, tool або data change |
| Test environment | agent sandbox / simulated environment | environment впливає на поведінку самого agent |
| Execution log | trajectory / trace | важливий не лише result, а шлях до result |
| Functional coverage | scenario / semantic / risk coverage | “кількість cases” набагато слабше характеризує coverage |
| Pass/fail | score distribution / threshold / confidence | quality часто статистична |
| Test data | eval dataset / adversarial set / production samples | сам dataset стає quality asset |
| Release regression | offline eval gate | необхідно контролювати stochastic variance |
| Production monitoring | continuous/online evaluation | production є частиною verification loop |

Саме **test oracle problem** стає центральним.

Для deterministic API `expected_status == 200` — чудовий oracle.

А який oracle для:

> “Дай коректну, релевантну, неупереджену відповідь, не розкривши sensitive information, правильно скористайся трьома tools і не зроби небезпечної irreversible action”?

Частину criteria можна перетворити на deterministic assertions. Частину — оцінювати правилами. Частину — LLM-as-a-judge. Частину — лише humans.

Anthropic прямо рекомендує змішувати різні graders і human calibration; Google підтримує як reference-based deterministic metrics, так і model-based raters та trajectory evaluation. citeturn21search0turn21search1

Отже, **quality engineer майбутнього дедалі більше стає engineer of test oracles**.

До цього додається statistical thinking. Навіть infrastructure може змінювати результати agentic eval. Anthropic у 2026 році показала, що resource limits та infrastructure errors впливали на benchmark scores coding agents, і прямо характеризує agentic evaluations як **end-to-end system tests**, де hardware, latency, resource configuration та infrastructure health можуть виступати confounders. citeturn21search4

Тобто для QE for AI стають нормальними concepts, які раніше були радше сусідніми дисциплінами:

**sampling, variance, confidence, experiment design, calibration, dataset representativeness, confounding factors.**

Є ще щонайменше п'ять великих вимірів, яких бракує моделі “просто тестування недетермінованого output”.

**Security.** Agent, на відміну від chatbot, може мати tools та real-world permissions. OWASP серед основних agentic threats виділяє Agent Behavior Hijacking, Tool Misuse/Exploitation та Identity/Privilege Abuse. Quality тут зливається з security engineering: недостатньо перевірити правильність відповіді — треба перевірити, чи agent узагалі мав право виконувати дію. citeturn21search2

**Data та provenance.** Якість AI application залежить не лише від model. Data validation була критичною ще для production ML до LLM, а NIST GAI profile включає provenance і lifecycle risk management у ширшу модель trustworthy AI. citeturn17search11turn21search3

**Drift.** Змінитися може model provider, prompt, index, retrieval corpus, tool API, user population або environment. Тому regression testing перетворюється на постійний process, а capability eval після стабілізації природно стає regression suite. citeturn21search0

**Observability.** Offline test suite ніколи не покриває весь production distribution, тому current agent platforms уже будують continuous production evaluation та analysis of historical traces як частину quality loop. Це фактично злиття традиційного QE з shift-right/SRE практикою. citeturn21search1turn21search9

**Governance та evidence.** ISO/IEC 25059 створила quality model для AI systems; ISO/IEC 42001:2023 визначає management system для governance AI risks; ISO/IEC TS 42119-2:2025 уже безпосередньо стандартизує підхід до testing AI systems. citeturn18search7turn7search1turn18search6

Регуляція посилює цей тренд. У ЄС із **2 серпня 2026 року** вже почалося enforcement застосовних положень AI Act і почали діяти transparency requirements; відповідно до актуальної timeline після змін Digital Omnibus, правила для high-risk systems Annex III мають застосовуватися з **2 грудня 2027 року**, а для high-risk AI, інтегрованого в regulated products Annex I, — з **2 серпня 2028 року**. citeturn19search2turn19search1

Практичний наслідок для професії величезний:

> частина майбутнього QE output — це не bug report і навіть не automated test.  
> Це **evidence**.

Наприклад:

- які risks були ідентифіковані;
- які eval datasets репрезентують їх;
- які thresholds встановлені;
- який результат повторних runs;
- чи тестували adverse conditions;
- які production metrics контролюються;
- хто може approve exceptional behavior;
- чи є audit trail;
- як система поводиться при model/tool/data change.

Саме тут твої дві гілки починають рекурсивно зростатися.

**QE with AI → QE for AI:**  
AI-agent, який створює та запускає тести, сам стає частиною test infrastructure і тому потребує validation.

**QE for AI → QE with AI:**  
кількість scenarios, outputs та trajectories настільки велика, що тестувати AI system практично неможливо без AI simulators, AI-generated data та AI judges.

Тобто:

> **AI тестує software → QE тестує AI → AI допомагає QE тестувати AI.**

До 2030 року це, на мою думку, стане одним continuous assurance loop.

Саме тому я додав би до твоєї моделі третій рівень:

> **QE with AI** — AI є інструментом QE.  
> **QE for AI** — AI є об'єктом QE.  
> **QE over AI** — AI є одночасно інструментом, об'єктом і autonomous actor усередині SDLC.

Остання назва — моя аналітична конструкція, а не усталений industry term. Але саме цей третій рівень, на мою оцінку, найкраще описує напрямок конвергенції, який уже простежується в agentic SDLC, AI eval tooling та emerging standards. citeturn23search1turn21search0turn18search6

## Найімовірніші сценарії професії QE до 2030 року

Прогнозувати AI на чотири роки вперед особливо небезпечно. Навіть METR зауважує, що benchmarks для frontier agents швидко насичуються, а productivity experiments буквально стає складніше проводити через зміну способу роботи developers. Тому коректніше прогнозувати не конкретні capabilities моделей 2030 року, а **структурні сили**, які вже діють: automation cost падає, agent autonomy зростає, AI features поширюються, evaluation стає окремою engineering discipline, regulation вимагає evidence, а organizations все ще сильно відрізняються за maturity. citeturn23search0turn22search3turn20search0

**Сценарій “Converged Quality / Trust Engineering” — приблизно 55%.**

Це моя базова модель.

Типова product team у 2030 році має кілька software-engineering agents, які можуть аналізувати issue, модифікувати codebase, створити implementation, додати tests, виконати CI, дослідити failure і запропонувати fix. Люди переважно керують intent, architecture, risk boundaries та approval. Сьогоднішня telemetry agentic coding уже показує подібний поділ planning versus execution, хоча це поки лише один vendor ecosystem. citeturn23search1

QE в такій команді більше не є основним author усіх tests.

Він проєктує **quality control plane**:

> business risks  
> → acceptance criteria  
> → deterministic invariants  
> → eval datasets  
> → automated graders  
> → adversarial scenarios  
> → agent simulations  
> → CI quality gates  
> → deployment policy  
> → production telemetry  
> → continuous evals  
> → incident feedback  
> → regression corpus.

Із traditional QE тут залишиться дуже багато. API, database, calculations, protocols, authorization rules та інші deterministic components усе ще краще перевіряти deterministic tests. Навіть Anthropic зазначає, що coding agents часто зручно оцінювати deterministic graders, оскільки generated software можна перевіряти тестами. citeturn21search0

Тобто AI не замінить traditional testing на evals.

Швидше виникне:

> **deterministic test pyramid + probabilistic eval layer + production assurance layer.**

На вершині цієї системи стоятиме risk-based human judgement.

У цьому сценарії назва “tester” поступово втрачатиме точність. Більш природними стануть ролі на кшталт **Quality Engineer, Quality Architect, AI Evaluation Engineer, AI Assurance Engineer, Agent Reliability Engineer, Trust Engineer**. Конкретні назви ще нестабільні; прогноз тут стосується функцій, а не job titles.

**Сценарій “довге співіснування двох QE” — приблизно 30%.**

Тут твоє початкове розділення зберігається майже до кінця десятиліття.

Одна велика категорія teams створює переважно deterministic enterprise software. Для них AI — перш за все productivity layer:

> QE with AI.

Інша категорія створює LLM products, autonomous agents, recommendation/decision systems, regulated AI тощо. Там формується окрема specialization:

> QE for AI / AI Evaluation / Model Validation / AI Assurance.

Цей сценарій цілком реалістичний через величезну різницю enterprise maturity. У World Quality Report 2025 лише 15% опитаних уже мали enterprise-wide GenAI scaling у QE, тоді як 43% залишалися на experimental stage; серед бар'єрів називали integration complexity, data privacy, skills та reliability concerns. citeturn20search0turn20search4

Регульовані industries також можуть прискорити спеціалізацію: EU AI Act має поетапне введення high-risk requirements до 2027–2028 років, а ISO вже створює окремий family of AI testing standards. Це сприяє появі людей, які знають саме AI assurance, evaluation, governance та conformity evidence. citeturn19search1turn18search6

Тобто convergence технологічно відбудеться, але organizationally професії можуть залишатися окремими значно довше.

**Сценарій “Autonomous SDLC compression” — приблизно 15%.**

Це найбільш disruptive варіант.

Якщо agent capabilities продовжать швидко зростати, software agent отримає task рівня:

> “Implement feature X according to these business constraints, update schema, migrate data, add tests, run security checks, deploy canary, inspect telemetry and fix regressions.”

Людина не пише ні implementation, ні більшість tests.

METR already вимірює frontier agent performance на задачах, людська складність яких лежить у багатогодинному діапазоні, хоча її верхні оцінки поки дуже невизначені. citeturn23search0

У такому світі execution-oriented QE headcount справді може різко скоротитися.

Особливо вразливими я вважаю tasks типу:

| Найсильніше стискаються | Чому |
|---|---|
| ручне написання стандартних test cases | generation має дуже низьку marginal cost |
| scripted manual regression | natural candidate for agent execution |
| boilerplate UI/API automation | coding agents добре працюють із локально перевірюваним code |
| routine test maintenance | agent бачить implementation + failures + tests одночасно |
| basic defect triage | класифікація та summarization добре автоматизуються |
| repetitive test-data preparation | GenAI/synthetic data уже активно використовується в QE |

Напрямок adoption цих use cases уже видно у World Quality Report, а сучасні coding agents демонструють дедалі більшу передачу execution decisions AI. citeturn20search3turn23search1

Але цей сценарій **не означає autonomous quality**.

Він створює принципову проблему:

> хто тестує tester-agent?

А якщо coding agent і testing agent використовують той самий foundation model або схожі training patterns — наскільки незалежними є їхні помилки?

Це означає, що в найавтоматизованішому сценарії залишаються дуже цінними маленькі senior QE/Assurance teams, які проєктують independent evaluation, adversarial validation, policies, environments, quality thresholds та production control.

Google's multi-agent experiments особливо добре демонструють, чому “просто додамо ще agents” не вирішує reliability: деякі coordination patterns покращують паралельні tasks, але погіршують sequential ones і можуть amplify errors. citeturn23search2

Отже, парадоксальний прогноз:

> **чим більше SDLC стане автономним, тим менше буде потреби в людях, які виконують тести, — але тим більш стратегічною стане роль людей, які визначають, що означає “достатньо перевірено”.**

Ринок праці також більше схожий саме на трансформацію, а не повне зникнення. BLS прогнозує +10% для Software QA Analysts/Testers у США в 2024–2034, а WEF одночасно очікує дуже значне skill disruption до 2030 року. Ці дві цифри чудово можуть співіснувати: **software demand росте, професія росте, але внутрішній набір задач професії змінюється радикально**. citeturn18search8turn18search1

Я б тому очікував приблизно таку зміну центру тяжіння:

| QE приблизно 2020 | QE приблизно 2026 | QE приблизно 2030 |
|---|---|---|
| “Я пишу tests” | “Я пишу tests разом з AI” | “Я визначаю систему verification, а agents реалізують значну її частину” |
| test automation | agent-assisted automation | autonomous quality workflows |
| expected results | assertions + AI assistance | assertions + eval rubrics + statistical acceptance |
| regression suite | generated/maintained suite | continuous eval ecosystem |
| pre-release testing | shift-left + shift-right | continuous assurance |
| defect detection | risk prevention | dynamic risk control |
| log analysis | AI-assisted triage | automated failure clustering + human escalation |
| tester of application | tester of system | evaluator of software + AI + agents + evaluators |
| quality metrics | pass rate / defects | business risk + reliability + safety + evidence |
| test framework | CI automation platform | quality/evaluation platform |

Найбільша зміна тут навіть не технологічна.

Це зміна **abstraction level професії**.

Tester працював із test steps.

Automation Engineer — із test code.

QE — із development process.

QE 2030 дедалі частіше працюватиме із **системою прийняття quality decisions**.

## Чого бракує моделі “QE with AI + QE for AI” і що варто будувати вже зараз

Твоє бачення, на мою оцінку, **правильне по напрямку, але приблизно на один abstraction level нижче від кінцевої трансформації**.

Ти бачиш:

> AI як інструмент  
> **+**  
> AI як об'єкт тестування.

Я б додав:

> **AI як autonomous participant у процесі створення самого software.**

Саме це змінює професію найбільше.

Коли AI просто допомагає написати Playwright test — це productivity improvement.

Коли AI сам вирішує, які tests потрібні, змінює implementation, запускає tests, аналізує failures, редагує test suite і приймає рішення “готово” — quality problem уже полягає не у test automation.

Проблема:

> **як побудувати governance над автономним engineering loop.**

Саме тому в DORA 2025 центральна теза — AI як amplifier існуючої engineering system, а не replacement цієї system. Хороші platform practices, version control, small batches, user focus і healthy data systems посилюють користь AI. citeturn22search1turn16view0

Звідси я бачу для сильного QE до 2030 року сім competency clusters.

| Компетенція | Чому вона дорожчатиме |
|---|---|
| **Risk & quality architecture** | AI легко генерує artifacts; набагато складніше правильно визначити, які failures мають значення |
| **Specification engineering** | agents потребують точніших goals, constraints, acceptance criteria та invariants |
| **AI evaluation engineering** | eval datasets, graders, repeated runs, human calibration, statistical acceptance стають аналогом нового test automation |
| **Agentic systems** | треба розуміти tool use, memory, trajectory, permissions, orchestration та failure propagation |
| **Data & observability** | quality стає continuous і production-driven |
| **Security & governance** | autonomous agents мають permissions і real-world side effects; regulation вимагає evidence |
| **Domain expertise & critical thinking** | саме high-context judgement найважче перетворити на дешеву generic automation |

Цей skill profile узгоджується з кількома незалежними сигналами. WEF ставить analytical thinking на перше місце серед core skills і AI/big data серед найшвидше зростаючих; World Quality Report одночасно високо оцінює GenAI skills, traditional QE skills та human/communication capabilities; emerging AI standards і EU regulation додають risk-management/governance dimension. citeturn18search1turn20search3turn18search6turn19search1

Особливо важливою я вважаю **specification engineering**.

Поточне покоління software engineering agents уже зміщує execution до AI, тоді як люди частіше залишають собі planning та визначення desired outcome. citeturn23search1

Це означає, що одна з найбільш цінних QE-skills 2030 року звучатиме дуже не по-тестувальницьки:

> **вміти точно визначити, що означає “correct”.**

Це включає:

business rules → invariants → risk taxonomy → acceptance criteria → testable properties → evaluation rubric → production SLO.

По суті, хороше requirements engineering, test design і domain knowledge зливаються.

Друга надзвичайно важлива компетенція — **evaluation engineering**.

Я б розглядав її як майбутнього спадкоємця test automation.

Test automation engineer 2015 року будував:

> framework + fixtures + test data + assertions + runner + reports.

AI Evaluation Engineer 2030 року будуватиме:

> eval framework + scenario corpus + synthetic users + environment simulator + deterministic graders + AI judges + calibration set + statistical thresholds + traces + production monitors.

Саме такі building blocks уже сьогодні з'являються у сучасних agent evaluation systems: multi-turn scenarios, user simulation, environment simulation, trace collection, trajectory evaluation, deterministic і model-based raters, production evaluation та failure clustering. citeturn21search1turn21search9

Третя компетенція — **statistics and experimental thinking**.

Не обов'язково ставати data scientist. Але QE для stochastic systems повинен інтуїтивно розуміти різницю між:

> “5 із 5 passes”  
> і  
> “95% estimated success rate із певною uncertainty”.

Між regression і noise.

Між model improvement і зміною environment.

Між representative eval dataset і benchmark overfitting.

Anthropic's infrastructure-noise research дуже наочно показує, що навіть benchmark score agent може змінитися через resource configuration; METR також проводить кілька незалежних runs на task і окремо перевіряє evaluation artefacts та reward hacking. citeturn21search4turn23search0

Четверта — **production quality / observability**.

У 2010-х shift-right був доповненням до testing. У AI-native systems я очікую, що він стане необхідністю: offline eval не може гарантувати поведінку на всій production distribution. Сучасні Google agent evaluation workflows уже прямо поділяються на rapid development evaluation, scheduled CI/CD regression та continuous online monitoring. citeturn21search9

Тобто до 2030 року стара дискусія:

> shift-left чи shift-right?

може значною мірою втратити сенс.

Більш правильна модель:

> **shift everywhere.**

Quality signal існує від requirements до production incident і назад у eval corpus.

П'ята — **security-aware QE**.

Коли software function повертає неправильне число — це defect.

Коли autonomous agent неправильно інтерпретує malicious instruction і має доступ до email, database, payments або production infrastructure — це вже потенційна security incident. OWASP's agentic guidance виділяє саме hijacking, tool misuse та privilege abuse як ключові класи ризиків. citeturn21search2

Тому межа між QE, AppSec і AI Safety стане значно менш чіткою.

Шоста — **governance та auditability**.

Сьогодні це можна сприймати як “enterprise overhead”. Але ISO 25059, ISO 42001 та нова ISO 42119 family, разом із уже чинним enforcement частини EU AI Act, показують іншу траєкторію: для значної кількості AI systems треба буде не просто *бути якісними*, а **мати доказ того, як quality/risk були оцінені та контрольовані**. citeturn18search7turn7search1turn18search6turn19search2

І сьома — **domain expertise**.

Це, можливо, найбільш недооцінена частина.

Коли написання test case коштує дорого, generalist tester, який уміє швидко створити багато cases, має очевидну цінність.

Коли AI може запропонувати 200 test cases за хвилину, цінність зміщується до людини, яка може сказати:

> “196 із них майже нічого не доводять. А ось цих чотирьох критичних scenarios тут взагалі немає”.

Саме тому результати Anthropic щодо agentic coding цікаві ще й іншим: higher task-specific expertise пов'язана з тим, як люди формулюють instructions, що вони просять agent перевіряти і наскільки здатні коригувати його поведінку. citeturn23search4

Тобто AI парадоксально може **підвищити, а не знизити relative value справжньої експертизи**.

Звідси я отримую приблизно таку формулу QE 2030:

> **QE 2030 = Quality Engineering fundamentals  
> + Software Engineering  
> + AI Evaluation  
> + Risk Engineering  
> + Observability  
> + Security  
> + Domain Expertise  
> + AI orchestration.**

Не кожному QE потрібно однаково глибоко знати всі ці області. Але “просто manual” проти “automation” перестає бути головною career fork.

Я очікую інші дві осі:

> **execution ←→ judgement**  
> **deterministic systems ←→ stochastic/agentic systems**

І найкраща career position — правий верхній кут:

> **високий judgement + здатність працювати з AI-native systems.**

З цього випливає ще один неприємний, але важливий прогноз: найбільший pressure AI створить не обов'язково на “manual testers” як людей, а на **роботу, яку легко специфікувати**.

Routine automation engineer, який здебільшого перетворює добре визначені cases у boilerplate code, потенційно не набагато захищеніший від coding agents, ніж manual QE, який виконує повторювану regression. Сучасні agentic coding systems уже забирають значну частину execution decisions, а AI use cases у QE рухаються до test design та requirements analysis. citeturn23search1turn20search4

Натомість exploratory testing не обов'язково зникне. Воно радше підніметься на abstraction level:

не

> “поклацати application і знайти баг”,

а

> “дослідити assumptions системи, сформувати novel hypotheses, знайти failure modes, яких немає в specification і eval corpus, а потім перетворити знахідки на executable evaluation”.

Це дуже схоже на цикл, який Anthropic рекомендує для agent evals: реальні failures стають новими eval cases, а capability tests із часом переходять у regression suite. citeturn21search0

Тому я б сформулював твою початкову тезу трохи інакше.

Не:

> **QE with AI + QE for AI → одна професія.**

А:

> **QE with AI + QE for AI + QE over AI-mediated SDLC  
> → Continuous Quality / AI Assurance Engineering.**

Саме **Continuous Assurance** тут є ключовим поняттям.

У класичному software testing ми намагалися довести:

> “цей build пройшов tests”.

У світі AI/agents цього дедалі частіше недостатньо.

Потрібно доводити щось значно складніше:

> “За наявними evidence ця версія системи, у цьому environment, із цими models/data/tools/policies, при заданому distribution of use та заданому risk appetite, поводиться достатньо надійно — і ми зможемо побачити, якщо це перестане бути правдою.”

Саме ця остання частина — **“ми побачимо, коли це перестане бути правдою”** — на мою думку, і відрізнятиме QE 2030 від QE 2020. Її вже видно в поєднанні offline evals, production monitoring, traces та continuous evaluation у сучасних agent frameworks. citeturn21search0turn21search9

І тому підсумкова оцінка твого бачення така:

**Ти правильно бачиш дві основні хвилі.** QE with AI автоматизує й підсилює нашу поточну роботу; QE for AI створює нову дисципліну перевірки stochastic systems.

**Ти також, на мою думку, правильно передбачаєш їхнє злиття до 2030 року.**

Але глобальна деталь, якої бракує, полягає в тому, що це злиття буде викликане не просто тим, що “тестувальникам доведеться і користуватися AI, і тестувати AI”.

Воно станеться тому, що:

> **сам SDLC перетворюється на AI-enabled distributed system, яку теж потрібно тестувати.**

Код стає output agent.

Tests стають output agent.

Test data стають output agent.

Diagnosis стає output agent.

Evaluator може бути agent.

Release decision частково може виконувати agent.

І отже, справжній system under test 2030 року — це вже **не application**.

Це:

> **product + models + data + agents + tools + pipelines + policies + humans + production environment.**

У такому світі найбільш стійка професійна ідентичність — не **“людина, яка тестує software”**.

Це **“людина, яка інженерно відповідає за довіру до поведінки software system”**.

І якщо сьогодні ми називаємо таку професію Quality Engineer, то до 2030 року слово **Quality** у цій назві, ймовірно, стане значно важливішим за слово **Testing**.