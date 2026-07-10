# @oasisomniverse/vue — OASIS Vue UI Component Library

The Vue 3 UI component library for the [OASIS Platform](https://oasisomniverse.one). 126 components covering avatar SSO, karma, NFTs, quests, map, seeds, messaging, OApps, providers and more — ready to use in any Vue or Nuxt project.

[![npm](https://img.shields.io/npm/v/@oasisomniverse/vue)](https://www.npmjs.com/package/@oasisomniverse/vue)
[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://oportal.oasisomniverse.one)

## Install

```bash
npm install @oasisomniverse/vue
```

## Basic Usage

Import components directly — no plugin registration needed:

```vue
<script setup>
import { Login, AvatarConnect, KarmaToast } from '@oasisomniverse/vue';
</script>

<template>
  <AvatarConnect />
  <KarmaToast />
  <Login @loggedIn="handleLogin" @switchTo="view = $event" />
</template>
```

Session state and API configuration are managed by the internal `useOasis()` composable, shared across all components automatically.

---

## Component Reference

### Auth & Identity

#### `<Login>`

Avatar login form. Emits navigation events to coordinate with your own auth flow.

```vue
<Login
  @loggedIn="handleLogin"
  @switchTo="view = $event"
/>
```

| Event | Payload | Description |
|---|---|---|
| `loggedIn` | — | Emitted on successful login |
| `switchTo` | `'signup' \| 'forgot'` | Emitted when the user clicks Sign Up or Forgot Password |

---

#### `<Signup>`

New avatar registration form.

```vue
<Signup @switchTo="view = $event" />
```

| Event | Payload | Description |
|---|---|---|
| `switchTo` | `'login'` | Emitted when the user clicks Sign In |

---

#### `<AvatarConnect>`

Login/logout toggle chip — fully self-contained. Manages session via `useOasis()` composable. No props or events required.

```vue
<AvatarConnect />
```

---

#### `<ForgotPassword>`

```vue
<ForgotPassword />
```

---

#### `<ResetPassword>`

```vue
<ResetPassword />
```

---

#### `<VerifyEmail>`

```vue
<VerifyEmail />
```

---

#### `<SearchAvatars>`

Search the OASIS avatar directory. Controlled via `:open`.

```vue
<SearchAvatars :open="showSearch" @close="showSearch = false" />
```

| Prop | Type | Default | Description |
|---|---|---|---|
| `open` | `boolean` | `false` | Controls visibility |

| Event | Description |
|---|---|
| `close` | Emitted when the panel should close |

---

### Avatar

Most avatar popups use `:open` / `@close`:

```vue
<ViewAvatar :open="show" @close="show = false" />
<EditAvatar :open="show" @close="show = false" />
<AvatarWallet :open="show" @close="show = false" />
```

---

### Karma

#### `<KarmaToast>`

Singleton toast — render once near your app root. Triggered automatically by `useOasis()` when karma changes.

```vue
<KarmaToast />
```

No props. Driven by internal composable state.

---

#### `<KarmaPanel>`

```vue
<KarmaPanel :open="show" @close="show = false" />
```

---

### Common UI

#### `<OasisModal>`

Controlled via `:open`.

```vue
<OasisModal :open="isOpen" @close="isOpen = false">
  <p>Modal content goes here.</p>
</OasisModal>
```

| Prop | Type | Default | Description |
|---|---|---|---|
| `open` | `boolean` | **required** | Controls visibility |
| `accentColor` | `string` | `'rgba(0,232,124,.25)'` | Border/accent colour |

| Event | Description |
|---|---|
| `close` | Emitted when the backdrop or close button is clicked |

---

#### `<NavBar>`

```vue
<NavBar />
```

---

#### `<StarField>`

```vue
<StarField />
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

Override CSS custom properties to theme components for your own OAPP:

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
