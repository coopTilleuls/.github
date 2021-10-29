# CSS

- Use a preprocesser (SASS ideally)
<!-- - use tailwind ? -->
- Graphic librairies :
  - From scratch ou small projects : in-house CSS & [bulma](https://bulma.io/)
  - For other projects : in-house CSS & [material UI](https://mui.com/)
  - How to organize you files : ITCSS (cf. [this (french) article by Grégory Copin](https://medium.com/dev-notes/just-do-itcss-1cb8a0c441d8))

<img src="https://lh3.googleusercontent.com/abUA-AZiXLfk9iUWZFD391If9omlZk-MIC1BvqALGVmNmZ1axZj8p4KYjTZ_a90Iz49yZsSRsL--lbB8tcBHYQCca_KvfUCCn3MOA0huujezMCQIbSsxsFa-vSfpmdh3N-0Ou8nd=s0" width=500>

- Naming convention :
  - use [BEM](http://getbem.com/naming/) naming
    Example:
    - .menu (BLOCK)
    - .menu\_\_item (ELEMENT)
    - .menu\_\_item-active (MODIFIER)

<img src="https://lh3.googleusercontent.com/dl-efulipYSZP6CrffFy4FBhxN_e_2EKNvyF_JgsPYLhGfjN5W7f7VG3zQitPQO_p9gDMNUhqT96KurhpsWmjvnw6IJ16mpTi-kYBqccZxzTdSFHUqmMyAsx7m3hoZp2PZnjTNKD=s0" width=500>

- Use selectors with low specificity

<img src="https://lh6.googleusercontent.com/vNnI6vBfEkTwMlovGBDIqwhsBUyHg_Fc48ij7mr0tZstMEcCoPHh7z4zj2YoRSgDuGiFKpDjskJ83JrpFJguhTDoqQ9JKCl8fTpvptbG-I14Xz_j13O5MfQS78NZI-UpvAYIxwPS=s0" width=200>
<img src="https://lh5.googleusercontent.com/Y3AsysPykPq_s99MsDAZhHz6DY-UzwUN5agPcur4w6V4242osHUUkGo2vYFOyK-JhwRFw15P3V_lsZiIYHCJBPrF5gP9az4xROZnp4fzTONFqAa_bP-P7oYIP5UEvaKEVRT5e7Ny=s0" width=200>

- Don't use IDs or element selector

<img src="https://lh6.googleusercontent.com/I8DLQgEgbox-njXvhSDlyLuOTPhYD8_C-exEkCjoEc8ByLmCto1l0acNpsSvDiNGqq2jx7T7udKKXDBmlQq2QMCvWNhEGNsSVTTuQFr97-j-9BcN6CRm5aPYUD6SuGmBifK3uv8m=s0" width=200>
<img src="https://lh4.googleusercontent.com/mO_dklSo-vzcUvRBFyz23Jm3HS_YlCX2y1Y_oOsqR0Zws3nduaAVxdfkNCqUj5LWvE58Eyj_O-2ErwSoh2RFFqzYO7skeMO2cwLstu8SDDrnJNXgLNuK6LxMSSQXBny9fLWiAtgb=s0" width=200>

- Don't depend on document Structure

<img src="https://lh6.googleusercontent.com/c6sQY4lzOCJYKw9kqm5hme9jNtdPiyqCh1_G-l6OtuFE1EtEK1MnDpVQNB3UnhcJuUUGco6iuIh1mZav22yhlWzRuve3vuZqaCAZcOAJHWYAs-h2fp5iUgyKt8FElV6wfyHmD6Xp=s0" width=200>
<img src="https://lh5.googleusercontent.com/koNDLHKfaXP1RlBC6YswaR4nGiEcQn5WFIuSTx8FR-ghmFJZ9-fmtjPv8-2XSw-kELUN4PNYCVvnDBo393rWjtQQEBG9DFXWKTUMQSFTe379DpRfseGXuhzxYcugLLdKIt1pDmWV=s0" width=200>

- Don't use inline styles or `!important`

  !important > inline style > #id > .class

- Write concise rules

<img src="https://lh3.googleusercontent.com/zRmCK2CasEGaW8dmsW_cdo-3GLV2N8zM5ud1J9hRTy3K5-MeLZiFcS6Le8X_19bWDfW9sMUpiW-8gmtaOTvnD07PF54J9dntIWsOPbEA3mNDyax7va51ZJRfwD_BtNKGkNJ9x0Bs=s0" width=300>
<img src="https://lh4.googleusercontent.com/20fCiBFXKDLKzspZ3n38QaePCY2D-pdVytKFgblXUHbI7c3mODObFGMfBSJ7vn_Fqf5xjK5UKV2UTumz0orW3sxEpRkWKsHAPtbxqUBS5PQCb--abpEpMANMb7Wlyy0ARwNeu3JP=s0" width=300>

# JS

## Factor to take into account when choosing the technical stack

- Team members’ level (senior vs. junior vs. "backend people in vacation doing frontend tasks")
- Does it have a lot of third-party dependancies ?
- Complexity of the SPA ?
- Performance of the SPA

## Stack pour internal projects

- Website : React + [NextJS](https://nextjs.org/)
- "Simple" application" : create-react-app (rewired) OR react + [gatsby](https://www.gatsbyjs.org/)
- "Performant" application : react + NextJS
- Mobile application: React Native
- Back-office: Angular, React-admin, Vue.js

## Quelques préconisations

- JS frameworks : react / vue / next.js / angular
- JS "flavor" (to adapt) : JS + Proptypes / Typescript / mix JS + Typescript
- JS facilitator : [create-react-app](https://github.com/facebook/create-react-app)
- State handling : [redux](https://redux.js.org/), ContextAPI
- Native : [react-native](https://facebook.github.io/react-native/)
- Test : [jest](https://jestjs.io/) (dont les mocks), [enzyme](https://airbnb.io/enzyme/)
- React specific : pattern Container/View, HOC, hook
- Forms : formik
- API fetching : axios, fetch
- COde linter : [prettier](https://prettier.io/), [es-lint](https://eslint.org/) (use and customize [Airbnb’s](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb))
- Importantly, use and abuse design patterns !
- SVG icons: <https://fontawesome.com/icons?d=gallery> (we have a licence)

# Reading resources

[ITCSS, by Grégory Copin](https://medium.com/dev-notes/just-do-itcss-1cb8a0c441d8)

[The Typescript tax](https://medium.com/javascript-scene/the-typescript-tax-132ff4cb175b)

[CSS for people hating CSS](http://paulcpederson.com/articles/css-for-people-who-hate-css/)
