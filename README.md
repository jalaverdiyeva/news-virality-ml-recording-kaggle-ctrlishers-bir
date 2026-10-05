# news-virality-ml-recording-kaggle-ctrlishers-bir 📠

bu layihe kaggle yarisi ucundur mashable dataseti uzerinde qurulub meqalenin viral olub olmuyacagini predict etmek ucun yazilib 📰

## proyektden umumi melumat 📄
demeli burda ~40k meqale var maşın öyrənməsi ile baxacaq ki meqale 1400 den cox paylasim alacaq yoxsa yox (target 1 ve ya 0)
kodun yarisini ozum yazmisam yarisini da ai komeyi ile iterate elemisem nece defe deyisib duzeltmisem bazi yerleri bir nece defe yeniden isletmisem hamsi kodun icinde var

## neynemisik detalni 🛻
- train csv yukledik baxtiq target nisbetine (~54.7% vs 45.3%) demek olar ki balancelidir
- skewness gore bazi numeric columnlara log1p verib duzeltdik kecdi 🤺
- categorical var idi weekday ve channel onlara one hot encoding verdik
- simpleimputer medina ile null doldurduq standardscaler ile scale eledik
- pca elave eledik azalsin correlated feature-lar ucun
- logistic regression qurduq sonra gradient boosting lightgbm yazdiq
- axirda da shap kitabxanasi isletdik ki baxaq model hansi feature cox onem verir

## lazim olan seyler 🥖
pip install pandas numpy matplotlib seaborn scipy scikit-learn lightgbm shap

## sonluq 🩵
test datasi daha sonranin tarixi oldugu ucun overfitting olmamasina cox diqqet elemisem ki gələcəkdəki meqaleleride yaxsi tapinsin
