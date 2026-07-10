# @oasisomniverse/vue — OASIS Vue UI Component Library

The Vue 3 UI component library for the [OASIS Platform](https://oasisomniverse.one). 126 components covering avatar SSO, karma, NFTs, quests, map, seeds, messaging, OApps, providers and more — ready to use in any Vue or Nuxt project.

[![npm](https://img.shields.io/npm/v/@oasisomniverse/vue)](https://www.npmjs.com/package/@oasisomniverse/vue)
[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://oportal.oasisomniverse.one)

## Install

```bash
npm install @oasisomniverse/vue
```

## Basic Usage

Register globally in `main.js`:

```js
import { createApp } from 'vue';
import OasisVue from '@oasisomniverse/vue';
import App from './App.vue';

const app = createApp(App);
app.use(OasisVue, { apiUrl: 'https://api.web4.oasisomniverse.one' });
app.mount('#app');
```

Or import components individually:

```vue
<script setup>
import { Login, AvatarConnect, KarmaToast } from '@oasisomniverse/vue';
</script>

<template>
  <Login @success="handleLogin" />
  <AvatarConnect @login="handleLogin" @logout="handleLogout" />
  <KarmaToast message="Quest completed" :amount="150" />
</template>
```

All components use the `apiUrl` passed to `app.use()`. Override per-component with `:apiUrl="'https://custom.api'"`.

---

## Component Reference

### Auth & Identity

#### `<Login>`

Avatar login popup/form.

```vue
<Login
  @success="handleLogin"
  @close="handleClose"
/>
```

| Prop | Type | Default | Description |
|---|---|---|---|
| `apiUrl` | `string` | from plugin install | OASIS API base URL override |

| Event | Payload | Description |
|---|---|---|
| `success` | `{ avatarId, username, karma }` | Emitted on successful login |
| `close` | — | Emitted when the popup is dismissed |

---

#### `<Signup>`

New avatar registration form.

```vue
<Signup @success="handleSignup" @close="handleClose" />
```

| Event | Payload | Description |
|---|---|---|
| `success` | avatar data object | Emitted on successful registration |
| `close` | — | Emitted when dismissed |

---

#### `<AvatarConnect>`

Login/logout toggle chip — manages session state automatically.

```vue
<AvatarConnect
  sessionKey="oasis_session"
  @login="handleLogin"
  @logout="handleLogout"
/>
```

| Prop | Type | Default | Description |
|---|---|---|---|
| `sessionKey` | `string` | `'oasis_session'` | sessionStorage key for login state persistence |

| Event | Payload | Description |
|---|---|---|
| `login` | `{ avatarId, username, karma }` | Emitted after login |
| `logout` | — | Emitted after logout |

---

#### `<ForgotPassword>`

```vue
<ForgotPassword @close="handleClose" />
```

---

#### `<ResetPassword>`

Password reset form — use with the token from the reset email link.

```vue
<ResetPassword :token="tokenFromRoute" @success="handleSuccess" />
```

| Prop | Type | Description |
|---|---|---|
| `token` | `string` | **Required.** Reset token from the email link |

---

#### `<VerifyEmail>`

```vue
<VerifyEmail :token="tokenFromRoute" @success="handleSuccess" />
```

---

#### `<SearchAvatars>`

```vue
<SearchAvatars @select="handleSelect" />
```

| Event | Payload | Description |
|---|---|---|
| `select` | avatar object | Emitted when the user picks an avatar |

---

#### `<SendInvite>` / `<AcceptInvite>`

```vue
<SendInvite @success="handleSuccess" />
<AcceptInvite :inviteCode="code" @success="handleSuccess" />
```

---

### Avatar

#### `<AvatarProfile>`

```vue
<AvatarProfile :avatarId="avatarId" @close="handleClose" />
```

| Prop | Type | Description |
|---|---|---|
| `avatarId` | `string` | Avatar to display — defaults to logged-in user |

---

#### `<ViewAvatar>`

```vue
<ViewAvatar :avatarId="avatarId" />
```

---

#### `<EditAvatar>`

```vue
<EditAvatar @success="handleSuccess" @close="handleClose" />
```

---

#### `<ViewAvatarKarma>`

```vue
<ViewAvatarKarma :avatarId="avatarId" />
```

---

### Karma

#### `<KarmaToast>`

Floating karma notification.

```vue
<KarmaToast message="Quest completed" :amount="150" />
```

| Prop | Type | Description |
|---|---|---|
| `message` | `string` | Reason text shown below the karma amount |
| `amount` | `number` | Karma delta — positive shown in cyan, negative in red |

---

#### `<KarmaPanel>`

```vue
<KarmaPanel @close="handleClose" />
```

---

### Map

```vue
<Map @close="handleClose" />
```

---

### NFT

```vue
<NFT :nftId="nftId" @close="handleClose" />
<PurchaseNFT :nftId="nftId" @success="handleSuccess" @close="handleClose" />
```

---

### OApp

```vue
<CreateOApp @success="handleCreated" @close="handleClose" />
<LaunchOApp :oappId="oappId" @close="handleClose" />
```

---

### Seeds

```vue
<Seeds @close="handleClose" />
<PayWithSeeds :amount="50" :recipientId="recipientId" @success="handleSuccess" @close="handleClose" />
```

---

### Common UI

#### `<OasisModal>`

```vue
<OasisModal title="My Modal" accentColor="#00c8ff" @close="handleClose">
  <p>Modal content goes here.</p>
</OasisModal>
```

| Prop | Type | Default | Description |
|---|---|---|---|
| `title` | `string` | `''` | Modal header title |
| `accentColor` | `string` | `'#00c8ff'` | Header accent colour |

| Event | Description |
|---|---|
| `close` | Emitted when dismissed |

---

#### `<NavBar>`

```vue
<NavBar :links="[{ label: 'Map', href: '/map' }]" />
```

---

#### `<Settings>` / `<Wallet>` / `<StarField>` / `<ComingSoon>`

```vue
<Settings @close="handleClose" />
<Wallet @close="handleClose" />
<StarField />
<ComingSoon label="Quests" />
```

---

## Full Component List

| Group | Components |
|---|---|
| **Auth & Identity** | AcceptInvite, AvatarConnect, ForgotPassword, Login, ResetPassword, SearchAvatar, SearchAvatars, SendInvite, Signup, VerifyEmail |
| **Avatar** | AvatarProfile, AvatarWallet, EditAvatar, SearchProfiles, ViewAchievements, ViewAvatar, ViewAvatarKarma, ViewLeagues, ViewOrganizations, ViewTournaments |
| **Data Screen** | ActivityPub, AddData, EOSIO, Ethereum, Holochain, IPFS, LoadData, ManageData, MongoDB, Neo4j, OffChainManagement, SearchData, Solana, Solid, SQLite, ThreeFold |
| **Eggs** | Eggs, ManageEggs, SearchEggs, ViewEggs |
| **Game** | Game |
| **Karma** | KarmaPanel, KarmaToast, SearchKarma, ViewKarma, VoteKarma |
| **Map** | Add2DObjectToMap, Add3DObjectToMap, AddQuestToMap, DownloadMap, ManageMap, Map, PlotRouteOnMap, SearchMap, ViewGlobal3DMap, ViewHalonsOnMap, ViewOAppOnMap, ViewQuestOnMap |
| **Messages** | MenuMessage, Message, MessageContacts, Messaging |
| **Mission** | ManageMission, Mission, SearchMission, ViewMission |
| **NFT** | ContactPopupNFT, ManageNFT, NFT, PurchaseNFT, PurchaseVirtualLandNFT, SearchNFT, ViewNFT |
| **OApp** | CreateOApp, DeployOApp, DownloadOApp, EditOApp, InstallOApp, LaunchOApp, ManageOApp, OApp, SearchOApp |
| **Providers** | CompareProviderSpeeds, CrossChainManagement, ManageAutoFailover, ManageAutoReplication, ManageLoadBalancing, ManageProviders, ProviderDropdown, Providers, SearchProviders, SeedsProvider, ViewProviderStats, ViewProviders |
| **Quest** | ManageQuest, Quest, SearchQuest, ViewQuest |
| **Seeds** | DonateSeeds, ManageSeeds, PayWithSeeds, RewardSeeds, SearchSeeds, Seeds, ViewSeeds |
| **Common UI** | ComingSoon, Confirmation, Contact, HyperDrive, NavBar, ONET, ONODE, OasisModal, Settings, SideNav, StarField, Wallet |

---

## Dark Space Design System

The OASIS component library ships with the **Dark Space** design system:

- **Background**: near-black (`#0a0d14`) with subtle nebula gradients
- **Primary accent**: electric cyan (`#00c8ff`)
- **Typography**: [Orbitron](https://fonts.google.com/specimen/Orbitron) for headings, [Rajdhani](https://fonts.google.com/specimen/Rajdhani) for body text
- **Text**: always bright (`#e0f0ff` / `#fff`) — never dim or faded
- **Borders**: translucent cyan (`rgba(0,200,255,0.2)`)
- **Cards**: glassy dark panels with `backdrop-filter: blur`

Override the CSS custom properties to theme components for your own OAPP:

```css
:root {
  --oasis-bg: #0a0d14;
  --oasis-accent: #00c8ff;
  --oasis-text: #e0f0ff;
  --oasis-border: rgba(0, 200, 255, 0.2);
}
```

---

## Live Demo

The Vue components are showcased in **[Noah's Ark Animal Rescue Network](https://github.com/NextGenSoftwareUK/NoahsArkAnimalRescueNetwork-Vue)** — a real-world OAPP built on this library.

See the full component matrix at **[oportal.oasisomniverse.one](https://oportal.oasisomniverse.one)**.

## Links

- [GitHub](https://github.com/NextGenSoftwareUK/OASIS-Vue-UI-Component-Library)
- [npm](https://www.npmjs.com/package/@oasisomniverse/vue)
- [OASIS API Docs](https://oasis-web4.gitbook.io/oasis-web4-docs/)
- [Developer Portal](https://oportal.oasisomniverse.one)
- [OASIS Platform](https://oasisomniverse.one)
