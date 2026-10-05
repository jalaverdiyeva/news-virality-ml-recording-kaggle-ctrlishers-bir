# news-virality-ml-recording-kaggle-ctrlishers-bir 📠

bu layihe kaggle yarisi ucundur mashable dataseti uzerinde qurulub meqalenin viral olub olmuyacagini predict etmek ucun yazilib 📰

## projeden umumi melumat 📄
demeli burda ~40k meqale var masin oyrenmesi ile baxacaq ki meqale 1400 den cox paylasim alacaq yoxsa yox (target 1 ve ya 0).
layihenin bashlangicini ozum yazmisam sonra ai ile birge iterate eleyib modeli qat-qat guclendirmisik.

## kodun inshaf merheleleri (menim kodum vs ai iterated) 🛻
- **birinci menim yazdigim hissə:**
  - train csv yukledim eda eledim target nisbetine baxdim (~54.7% vs 45.3% balansli idi)
  - numeric column-larda skewness > 1.5 olanlara log1p verib duzeltdim 🤺
  - categorical variable-lara (weekday, channel) one hot encoding verdik
  - pipeline icinde simpleimputer, standardscaler ve pca qurdum
  - baseline kimi logistic regression ve sadə lightgbm qurdum, shap waterfall ile 10-cu meqaleni izah eledim

- **sonra ai ile iterate elediyimiz hissə:**
  - **feature engineering:** deyishenlerin nisbetinden yeni feature-lar yaratdiq (`words_per_img`, `kw_avg_ratio`, `polarity_interaction`, `is_weekend` ve s.)
  - **cross validation:** dataseti sadece train/test bolmek evezine 5-fold stratified k-fold cv tətbiq eledik
  - **multi-model ensemble:** lightgbm ile yanaşı catboost classifier və xgboost classifier modellerini elave eledik 🥖
  - **rank averaging:** modellerin ehtimallarini birbaşa toplamaq evezine rankdata ile siralamaya cevirib (45% lgb + 35% cat + 20% xgb) harmanladiq ki roc-auc skoru max olsun

## lazim olan kitabxanalar 🥖
pip install pandas numpy matplotlib seaborn scipy scikit-learn lightgbm catboost xgboost shap

## sonluq 🩵
test datasi daha sonranin tarixi oldugu ucun overfitting olmamasina cox diqqet elemisem, ona gore k-fold ve rank ensemble cox komek eledi gələcəkdəki meqaleleri daha deqiq tapmaq ucun.
