## Modelli usati nel progetto
- <font size=4>Regressione Lineare </font> Multivariata
- <font size=4>Random Forest Regression </font>
- <font size=4>SVM => Support Vector Machine </font>
## Obbiettivo ML
<font size=4>il ML è applicabile a qualsiasi problema in cui ci sono dati sufficienti con l'obbiettivo di scoprire un modello di conoscenza => funzione che associ ad ogni dato di input  una classe/valore numerico. </font>
# Regressione Lineare
- <font size=4>1 variabile => regressione univariata </font>
![[regLineareUnivariata.png]]
- <font size=4>N variabili => regressione multivariata </font>
![[RegLineareMultivariata.png]]
<font size=4>La funzione ha dei parametri i cui valori devono essere determinati in modo diretto o numericamente:</font>
- <font size=4>Metodo Diretto => soluzione ottima ma richiede delle operazioni di costo </font>$O(N^3)$<font size=4> il che lo rende inadeguato per grandi bacini di dati ed impossibile da mettere in pratica per big data, inoltre è una soluzione ideale solo per problemi convessi.</font>
- <font size=4>Metodo Numerico => discesa del gradiente, non garantisce soluzioni ottime, ma è parallelizzabile, incrementale e usabile anche per problemi non convessi.</font>
### MSE => Mean Squared Error (Reg Lineare Univariata) 
<font size=4>Misura Standard per l'errore della regressione :</font>$$errore = \frac{1}{m}\sum_{i=1}^{m}{(\hat{y_i}-y_i)^2}$$La funzione del MSE viene usata come la funzione dei parametri del modelli (funzione usata per trovare i valori dei parametri), in questo modo se tracciamo la dunzione dell'errore $E$ su $n$ parametri si ottiene una curva in $n+1$ dimensioni come quella che segue:
![[errorCurve.png]]
### L'obbiettivo della Regressione 
L'obbiettivo è quindi trovare i parametri nei quali l'errore calcolato è il minimo, il vertice della parabola quindi.
E per trovare ciò utilizziamo il gradiente di una funzione che equivale al vettore delle derivate parziali della funzione f per ciascuna delle sue variabili, questo perché il gradiente, nel grafico, rappresenta <strong>l'inclinazione della curva nel punto x su cui viene calcolato</strong>.
	Dal Gradiente si può quindi determinare in quale punto della funzione la direzione della curva dell'errore scende o sale più rapidamente.
#### Discesa del Gradiente (Reg Lineare Univariata)
Metodo iterativo per trovare un minimo locale di una funzione seguendo il gradiente:
![[GradientDescent.png]]
il punto 3 di fatto esegue questa formula: $$x_{k+1} = - \eta\ * \nabla{f}{(x_k)}$$dove $\eta$ è un iperparametro chiamato learning rate oppure step size, rappresenta la lunghezza del passo di discesa fatto ad ogni iterazione.
### Regressione Lineare Multivariata (*Progetto*)
Il Modello generale è il seguente:$$h_{\theta}(x_1,...,x_n) = \theta_0+\theta_1*x_1 + ... +\theta_n*x_n  $$
Dove $\theta$ corrisponde hai pesi delle singole variabili sulla predizione, $\theta_0$ è il valore da restituire quando $x=0$, detto anche intercetta.
In forma vettoriale è così $h_\theta(x) = \theta_0 +\theta*x$ con $x = [x_1 ... x_n]$ oppure anche così che è più compatto:$$
    \begin{cases}
      h_\theta(x) = \theta * x\\
      x = [1,x_1 ...x_n]
    \end{cases}$$
#### Errore Quadratico Medio (Reg Lineare Multivariata)
In forma vettoriale è come segue:$$E(\theta) = \frac{1}{m}\sum_{i=1}^m{(\theta*x_i-y_i)^2}$$
che rappresenta l'equivalente di quello per la Reg Lineare Univariata solo fatto su tutte le singole equazioni di tutte le $n$ variabili.
#### Discesa del Gradiente (Reg Lineare Multivariata)
##### Rappresentazione in forma matriciale
Per scrivere di meno le variabili di input (x) e le variabili di output (y) possono essere rappresentate sottoforma di matrici:
- Matrice X => ogni riga rappresenta una riga della tabella del dataset, ed ogni colonna una feature (variabile $x_i$) da dare in pasto al modello, ne viene inserita una che rappresenta l'intercetta $\theta_0$ con valore costante.
- Matrice Y => matrice 1 colonna x n righe della matrice X, rappresenta le predizioni associate per numero di riga.
- Matrice $\theta$ => anche lei come Y è una matrice colonna, contiene tutti i pesi associati alle feature.
##### Discesa Grad
Questo è il gradiente dell'errore:$$\nabla{E(\theta) = \frac{2}{m}X^T(\theta*X-Y)}$$
Allora la formula per l'aggiornamento del "punto"(fase 3 dell'interazione dell'algoritmo Gradient Descent) , in questo scope non è più un punto ma un vettore:$$\theta_{k+1} = \theta_k-\frac{2*\eta}{m}X^T(\theta_k*X-Y)$$
### Normalizzare una variabile
Per normalizzare una variabile si esegue la seguente formula$$\tilde{x}=\frac{x-min(x)}{max(x)-min(x)}$$
Ovviamente se si normalizzano i dati, poi gli output vanno denormalizzati.
### Coefficiente $R^2$
Indica la proporzione di variazione della variabile dipendente che è predicibile dalle variabili indipendenti.
Detto in parole povere => Indica quanto varia la y in base alle x.
Calcolato nel seguente modo:$$R^2 = \frac{\sum^m_{i=1}{(\hat{y}_i-\overline{y})^2}}{(y_i-\overline{y})^2}$$
dove $\hat{y_i}$ è la i-esima previsione, $y_i$ è la i-esima corretta previsione e $\overline{y}$ è il valore medio delle $y$.
Oscilla tra i seguenti valori $[0 ... 1]$ con i seguenti significati:
- 1 => il modello descrive perfettamente i dati
- 0 => tra il modello ed i dati non vi è alcuna correlazione
- valori intermedi indicano diversi gradi di efficacia del  modello.
#### Intervallo di Confidenza (CI)
$$CI = R^2 +- t * \sqrt{VR}$$ dove:
- $t$ => è dato dal livello di confidenza e dal numero di istanze (numero dei dati)
- $VR$ è la Varianza data da: $$\frac{4*R^2*(1-R^2)^2 *(n-k-1)^2 }{(n^2-1)*(n+3)}$$
	Dove $n$ è il numero di istanze del test set e $k$ il numero di variabili di input.
- e $\sqrt{VR}$ rappresenta l'errore standard, anche chiamata deviazione standard.
## Regressione Non Lineare (Polinomiale)
La regressione polinomiale è una generalizzazione di quella lineare con altri termini di grado superiore, usata per ottenere modelli capaci di descrivere dataset più complessi.
Regressione Polinomiale Univariata di grado 3: $$h(x)=\theta_0+\theta_1x+\theta_2x^2+\theta_3x^3$$
Regressione Polinomiale multivariata di grado 2:$$h(a,b)= \theta_0+\theta_1a_1+\theta_2a^2+\theta_3b+\theta_4ab+\theta_5b^2$$
### Regolarizzazione => Ridge Regression
Il grado della regressione polinomiale misura la complessità del modello di learning, il vero problema è che i coefficienti del polinomio provocano una forte oscillazione peggiorando l'accuratezza.
Quindi la <strong>regolarizzazione</strong> punta a ridurre il valore dei coefficienti nel seguente modo:
Viene aggiunto alla funzione d'errore da minimizzare anche $\lambda*\theta$ dove $\lambda$ è un iperparametro $-0\leq \lambda<\infty$   
### Funzione Kernel
Una funzione kernel è una funzione che misura la somiglianza tra due dati, permettendo di calcolare il prodotto scalare in uno spazio ad alta (infinita) dimensione senza dover esplicitamente trasformare quei dati e memorizzarli.
Ne esistono diversi tipi, RBG (Gaussian Radial Basis Function) è uno fra questi.
#### RBF (Usata nel progetto per SVM)
![[RBFKernel.png]]
Ricordiamo che $(x-\mu^i)^2$ è la distanza euclidea.
## Alberi di Regressione
![[RegressionTree.png]]
![[RegressionTree2.png]]
La complessità del modello in questo caso è direttamente proporzionale alla profondità dell'albero, però più è profondo, quindi complesso, e più possiamo avere dell'overfitting.
Per evitarlo possiamo utilizzare la regolarizzazione vista nella Regressione lineare.
#### Strategie per creare l'albero
1. lasciare crescere l'albero fino a che la loss function aumenta
2. lasciare crescere completamente l'albero, quindi renderlo il più complesso possibile, per poi andarlo a potare fino a quando la loss torna ad aumentare
#### Regole di Potatura
Basta potare quando:
- ogni foglia contiene una sola istanza o un numero di istanze inferiore ad una soglia (iperparametro).
- il numero di foglie è inferiore ad una soglia o quando l'errore nella foglia è inferiore ad una soglia.
- il p-value della differenza tra le due regressioni ottenute nella divisione di un nodo in 2 foglie è maggiore di una soglia in base ad un test statistico (t-test Student).
Caso in cui l'albero fa delle classificazioni:
- Basta potare quando tutte le istanze di una foglia hanno la stessa label.
##### T-Test Student
è il test statistico di cui sopra, e serve per testare a livello statistico se le differenze fra due foglie siano date dal caso oppure siano significative, sono date dal caso solamente quando $t\\-value > soglia$, la soglia è scelta arbitrariamente.
Possiamo definire anche p-value, che è la probabilità che la differenza tra i due gruppi sia frutto del caso.
Quindi possiamo dire che t-value e p-value siano inversamente proporzionali.
Medie delle foglia sinistra ($<$) e destra ($\geq$): 
$$\overline{y}_< = \frac{\sum_{i\in{S_{j,<}}}y_i}{|S_{j,<}|} , \overline{y}_\geq = \frac{\sum_{i\in{S_{j,\geq}}}y_i}{|S_{j,\geq}|}$$
Varianza:$$\sigma^2_{\overline{y}_<} = \frac{\sum_{i\in S_{j,<}}(y_i-\overline{y}_<)^2}{|S_{j,<}|-1} , \sigma^2_{\overline{y}_\geq} = \frac{\sum_{i\in S_{j,\geq}}(y_i-\overline{y}_\geq)^2}{|S_{j,\geq}|-1}$$ 
$$t-score = \frac{\overline{y}_< - \overline{y}_\geq}{\sqrt{\frac{\sigma^2_{\overline{y}_<}}{|S_{j,<}|}-\frac{\sigma^2_{\overline{y}_\geq}}{|S_{j,\geq}|}}}$$
## Foreste di Regressione
Normalmente l'errore diminuisce combinando diversi alberi semplici, creati sullo stesso dataset (Ensemble Learning):
- vengono utilizzati per ciascun albero un sottoinsieme casuale non disgiunto, bagging o boostrap aggregating, e sottoinsiemi casuali di variabili di input (RANDOM FOREST)
	![[RandomForestBaseSystem.png]]
- alberi in sequenza da errori residui del precedente: gradient boostring, xgboost ...
	Il funzionamento base è quello di un Training Additivo di modelli, perchè:
	![[SequenceTrees.png]]
# Classificare
Significa trovare una funzione che massimizzi la separazione tra le classi.
![[ClassifierIperpiano.png]]
Dove $w$ è il vettore colonna $n \times 1$ dei coefficienti delle variabili di input, $n$ è il numero di variabili di input, $w$ prende anche il nome di vettore dei pesi.
$b$ invece è il bias o intercetta, quindi è il valore di default quando $x=0$.
La distanza da l'iperpiano, ovvero la retta formata da $w^Tx+b=0$, di un qualsiasi punto viene calcolata così:$$d = \frac{w^Tx+b}{||w||}$$
#### Come i classificatori trovano l'iperpiano
- Perceptron, Regressione Logistica e Regressione Lineare con soglia (e altri) trovano un iperpiano di separazione non ottimale, la ricerca di questo iperpiano viene influenzata da tutti i punti sul piano.
- SVM invece trova un iperpiano di separazione ottimale utilizzando per la ricerca solo i "punti difficili" ovvero quelli vicini al decision boundart. 
### Classificatori Non Lineari
ci sono due scuole di pensiero:
- Soluzioni che trasformano lo spazio dei dati in modo che le classi diventino separabili linearmente => SMV, Reti Neurali ...
- Soluzioni intrinsecamente non lineari => Decision Tree, RandomForest, Gradient Boosting, XGboost.
In generale più variabili hanno i dati e più sono separabili linearmente.
### Classificatori Lineari
#### Perceptron 
Antenato delle Reti Neurali.
Il Perceptron di default lavora con 2 classi, quindi è un classificatore binario, proprio per questo possiamo dire che: $$y = \begin{cases}
-1 \ if\ class\ A  \\ +1\ if\ class\ B 
\end{cases}$$

dove $y$ è l'etichetta.
La forma compatta è la seguente => $-y(b+wx)<0$ 
Che volendo possiamo anche fare che $$-y(b+wx)<0 <==> max(0,-y(b+wx)) = 0$$
dove la seconda restituisce 0 se la classe viene predetta correttamente, altrimenti il valore è positivo.
Quindi per minimizzare l'errore, rispetto a $b$ e $w$, avremo che la somma della espressione sulle $m$ istanze di training  è come segue:$$minimize_{b,w} \sum_{i=1}^m{max(0,-y_i*h_w(x_i))} \ \ \ \ \ \ \ dove \ h_w(x_i) = b+wx_i$$
##### PROBLEMA
La funzione è continua e convessa ma NON derivabile quindi il gradient descent sappiamo tutti quanti dove ce lo possiamo infilare!
##### Soluzione
fanculo sostituiamo la funzione con una sua approssimazione che è anche derivabile
$$softmax(0,S) = log(1+e^S)$$
ed ora dobbiamo minimizzare $$minimize_{b,w} \sum_{i=1}^m{log(1+e^{-y_i*h_w(x_i)})}$$
funzione nota come <strong>Logisti Loss</strong> alla quale possiamo aggiungere il membro della regolarizzazione   $$minimize_{b,w} \sum_{i=1}^m{log(1+e^{-y_i*h_w(x_i)})}+\frac{\lambda}{2}||w||^2_2$$
### Regressione Logistica
Viene fatta la derivata della logistic loss con norma L2(quella sopra) e poi al risultato vengono determinati die parametri w migliori con discesa del gradiente ottenendo$$\tilde{w}=\tilde{w}-\eta(\sum^m_{i=1}-\frac{y_i\tilde{x}}{1+e^{y_i*h_w(\tilde x_i)}}+\lambda\tilde{w})$$
dove le $\sim$ stanno ad indicare dei vettori regolarizzati.
Fatta sta roba abbiamo la <strong>sigmoid</strong>:$\sigma(h_\tilde{w}(\tilde{x})) = \frac{1}{1+e^{-(b+wx)}} \ \ \ \ \ \ \ dove \ b+xw$ è l'iperpiano individuato.
### Classificazione Multiclasse con iperpiani 
2 metodi:
- One-Versus-All 
- Multinomial
#### One-Versus-All
Viene individuato un iperpiano per classe:$$b_c+x^Tw_c = 0,\ c=1 ... C$$
Dove $C$ è il numero di iperpiani, quindi il numero di classi.
Ad ogni istanza $x$ si assegna la classe $y$ corrispondente al piano $j$ che massimizza:$$y=argmax_{j=1 ... C} \ b_j+x^Tw_j$$
#### Multimodal
![[MultimodalClassifier.png]]
### Problema Classi Sbilanciate
![[SbilanciateCLasses.png]]
## Stabilire l'iperpiano migliore
l’iperpiano individuato da Perceptron e Regressione Logistica è uno dei tanti possibili iperpiani di separazione.
![[miglioreSuperpiano.png]]
![[svmDefinitionP.png]]
$p$ viene trovato summando le due distanze dei support vectors $s_1,s_2$ quindi:$$\frac{|w^Ts_1+b|}{||w||}+\frac{|w^Ts_2+b|}{||w||} = \frac{1}{||w||}+\frac{1}{||w||} = \frac{2}{||w||} = p$$
le prime due formule sono le formule delle distanze da $s_1$ e $s_2$ come spiegato [[#Classificare]].
Inoltre bisogna dire che b (bias, intercetta) descrive quanto l'iperpiano $w^Tx+b=0$ sia distanze dall'origine del piano cartesiano perchè il punto dell'origine $(0,0)$ sottintende che $w^Tx=0, x=0$ e quindi $d=\frac{b}{||w||}$.
![[finalSVMClassifierFunction.png]]
![[multiclassSVM.png]]
![[softMargin.png]]
### SVM non Lineare
SVM prima riusciva a dividere linearmente i dati perchè erano separabili, ma con dati non separabili linearmente dobbiamo mapparli in uno spazio con maggiori dimensioni dove diventano divisibili linearmente.
Il mapping viene fatto tramite una funzione non lineare:
![[SVM non lineari.png]]
![[OttimizationSvmNonLinear.png]]
dove $C\sum_i\xi_i$ è la somma delle variabili di slack ($\xi \geq 0 , per \ ogni \ i$)
#### PROBLEMA => Maledizione della Dimensionalità
![[Maledizione.png]]
Perchè si ottiene che $nOperazioni =O(\frac{1}{2}n(n+1))$ dove $n =$ dimensione dello spazio iniziale.
Quindi in generale trasformazioni con polinomi di grado $g$ costano $\cong O(\frac{n^g}{g!})$  
![[BigProblemMyGuy.png]]
### Soluzione => Kernel Trick
Kernel Polinomiali $K(x,z) = (x*z)^g$ , per non usare $\phi(x) * \phi(z)$ che comporta un enorme costo computazionale per via delle operazioni con i vettori trasformati($\phi$).
![[kernel.png]]
![[teorema.png]]
![[kernelsss.png]]
#### Iperparametri C e $\gamma$ 
`C` è il **parametro di penalizzazione degli errori di classificazione**.    
Bilancia il **margine massimale** (quanto grande è la separazione tra classi) con **gli errori di classificazione** (quanto bene si adattano i dati):
- **`C` grande** (es: 1000):
    
    - Il modello cerca di **classificare tutto correttamente** → margine più piccolo.
        
    - **Overfitting** possibile: si adatta molto ai dati di training.
        
- **`C` piccolo** (es: 0.01):
    
    - Il modello **accetta alcuni errori** → margine più grande.
        
    - **Generalizza meglio**, ma potrebbe fare errori sui dati di training.
---
### Gamma si usa **solo con kernel non lineari** (es: RBF, polinomiale).

- È un parametro interno del **kernel RBF (Gaussiano)**:
    
    K(x,x′)=exp⁡(−γ∥x−x′∥2)K(x, x') = \exp\left(-\gamma \|x - x'\|^2\right)K(x,x′)=exp(−γ∥x−x′∥2)

### ➤ Cosa succede se:

- **`gamma` grande** (es: 10):
    
    - Ogni punto ha un'influenza molto **locale** (piccola "bolla").
        
    - Il modello può diventare **molto complesso** → **overfitting**.
        
- **`gamma` piccolo** (es: 0.01):
    
    - Ogni punto ha un’influenza più **globale** (grande "bolla").
        
    - Il modello è più **liscio**, meno sensibile → **underfitting** possibile.