# CSS

- utiliser un pré-processeur (SASS idéalement)

- librairies graphiques :

- from scratch ou petits projets : CSS maison & [bulma](https://bulma.io/)

- pour les autres projets : CSS maison & [material UI](https://material-ui.com/fr/)

- organisation des fichiers : ITCSS (cf. [l'article de Grégory Copin](https://medium.com/dev-notes/just-do-itcss-1cb8a0c441d8))

![](https://lh3.googleusercontent.com/abUA-AZiXLfk9iUWZFD391If9omlZk-MIC1BvqALGVmNmZ1axZj8p4KYjTZ_a90Iz49yZsSRsL--lbB8tcBHYQCca_KvfUCCn3MOA0huujezMCQIbSsxsFa-vSfpmdh3N-0Ou8nd=s0)

- convention de nommage :

- utiliser la notation [BEM](http://getbem.com/naming/)

Exemple:

- .menu (BLOCK)

- .menu\_\_item (ELEMENT)

- .menu\_\_item-active (MODIFIER)

![](https://lh3.googleusercontent.com/dl-efulipYSZP6CrffFy4FBhxN_e_2EKNvyF_JgsPYLhGfjN5W7f7VG3zQitPQO_p9gDMNUhqT96KurhpsWmjvnw6IJ16mpTi-kYBqccZxzTdSFHUqmMyAsx7m3hoZp2PZnjTNKD=s0)

- utiliser des sélecteurs avec spécificité faible

![](https://lh6.googleusercontent.com/vNnI6vBfEkTwMlovGBDIqwhsBUyHg_Fc48ij7mr0tZstMEcCoPHh7z4zj2YoRSgDuGiFKpDjskJ83JrpFJguhTDoqQ9JKCl8fTpvptbG-I14Xz_j13O5MfQS78NZI-UpvAYIxwPS=s0) ![](https://lh5.googleusercontent.com/Y3AsysPykPq_s99MsDAZhHz6DY-UzwUN5agPcur4w6V4242osHUUkGo2vYFOyK-JhwRFw15P3V_lsZiIYHCJBPrF5gP9az4xROZnp4fzTONFqAa_bP-P7oYIP5UEvaKEVRT5e7Ny=s0)

- Ne pas utiliser d'ID ou de sélecteur d'élément

![](https://lh6.googleusercontent.com/I8DLQgEgbox-njXvhSDlyLuOTPhYD8_C-exEkCjoEc8ByLmCto1l0acNpsSvDiNGqq2jx7T7udKKXDBmlQq2QMCvWNhEGNsSVTTuQFr97-j-9BcN6CRm5aPYUD6SuGmBifK3uv8m=s0)![](https://lh4.googleusercontent.com/mO_dklSo-vzcUvRBFyz23Jm3HS_YlCX2y1Y_oOsqR0Zws3nduaAVxdfkNCqUj5LWvE58Eyj_O-2ErwSoh2RFFqzYO7skeMO2cwLstu8SDDrnJNXgLNuK6LxMSSQXBny9fLWiAtgb=s0)

- Ne pas dépendre de la structure du document

![](https://lh6.googleusercontent.com/c6sQY4lzOCJYKw9kqm5hme9jNtdPiyqCh1_G-l6OtuFE1EtEK1MnDpVQNB3UnhcJuUUGco6iuIh1mZav22yhlWzRuve3vuZqaCAZcOAJHWYAs-h2fp5iUgyKt8FElV6wfyHmD6Xp=s0)![](https://lh5.googleusercontent.com/koNDLHKfaXP1RlBC6YswaR4nGiEcQn5WFIuSTx8FR-ghmFJZ9-fmtjPv8-2XSw-kELUN4PNYCVvnDBo393rWjtQQEBG9DFXWKTUMQSFTe379DpRfseGXuhzxYcugLLdKIt1pDmWV=s0)

- Ne pas utiliser les styles inline ni !important

!important > inline style > #id > .class

- Écrire des règles concises

![](https://lh3.googleusercontent.com/zRmCK2CasEGaW8dmsW_cdo-3GLV2N8zM5ud1J9hRTy3K5-MeLZiFcS6Le8X_19bWDfW9sMUpiW-8gmtaOTvnD07PF54J9dntIWsOPbEA3mNDyax7va51ZJRfwD_BtNKGkNJ9x0Bs=s0)![](https://lh4.googleusercontent.com/20fCiBFXKDLKzspZ3n38QaePCY2D-pdVytKFgblXUHbI7c3mODObFGMfBSJ7vn_Fqf5xjK5UKV2UTumz0orW3sxEpRkWKsHAPtbxqUBS5PQCb--abpEpMANMb7Wlyy0ARwNeu3JP=s0)

# JS

## Facteur à prendre en compte dans le choix de la stack technique

- niveau de l'équipe (senior vs. junior vs. "les backs qui font du front")
- beaucoup de dépendances tierces ?
- SPA complexe ?
- performance de la SPA

## Stack pour les projets en interne aux Tilleuls

- site : react + [NextJS](https://nextjs.org/)
- application "simple" : create-react-app (rewired) OU react + [gatsby](https://www.gatsbyjs.org/)
- application "performante" : react + NextJS
- application mobile : react-native
- back-office : angular, react-admin

## Quelques préconisations

- framework JS : react / vue / next.js / angular
- JS "flavor" (s'adapter pour ne pas alourdir à outrance) : JS + Proptypes / Typescript / mix JS + Typescript
- facilitateur JS : [create-react-app](https://github.com/facebook/create-react-app)
- gestion du state : [redux](https://redux.js.org/), ContextAPI
- natif : [react-native](https://facebook.github.io/react-native/)
- test : [jest](https://jestjs.io/) (dont les mocks), [enzyme](https://airbnb.io/enzyme/)
- spécifique à React : pattern Container/View, HOC, hook
- formulaires : formik
- fetch d'API : axios, fetch
- vérificateurs de code : [prettier](https://prettier.io/), [es-lint](https://eslint.org/) (prendre [celui d'Airbnb](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb) et customiser par-dessus)
- et surtout : abuser des design pattern !
- icônes SVG: <https://fontawesome.com/icons?d=gallery> (on a une licence pro)

# Ressources (à lire)

[ITCSS par Grégory Copin](https://medium.com/dev-notes/just-do-itcss-1cb8a0c441d8)

[Les coûts induits par Typescript](https://medium.com/javascript-scene/the-typescript-tax-132ff4cb175b)

[CSS pour les gens qui détestent le CSS](http://paulcpederson.com/articles/css-for-people-who-hate-css/)
