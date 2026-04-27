# Astro Mobile Buyer DS — Library Reference

## File Keys

| Library | File Key |
|---|---|
| Astro Mobile Buyer DS (components, icons, variables) | `LD5Y3L9vAvw3MAU2POgseI` |
| Astro Illustration library | `tWd29HOmovgLvK5NdqbxB0` |

---

## Color Variables — `figma.variables.importVariableByKeyAsync(key)`

Apply with:
```js
const colorVar = await figma.variables.importVariableByKeyAsync("<key>");
node.fills = [{ type: "SOLID", boundVariables: { color: { type: "VARIABLE_ALIAS", id: colorVar.id } } }];
```

### TextColor
| Token | Key |
|---|---|
| `TextColor/PrimaryDark` | `033e4d8dbf3c235f253562e65640addd37a804e0` |
| `TextColor/SecondaryDark` | `dc4832ded7daf1efd20201f6ae4d981de93b5eca` |
| `TextColor/Placeholder` | `57dd8435d5e70c3739c0e3079a5c6fd3df15aa22` |
| `TextColor/Disable` | `80470fe0d99673abd19139d6b3fcbdb6b9e23940` |
| `TextColor/Link` | `673d55d2c663b391b6da6177e0854f2ded2fcdee` |
| `TextColor/LinkHover` | `0950f4954c99ddac8aa4d1ad803141e373edbfcb` |
| `TextColor/LinkSelected` | `cd948f56c40aae300bf30bd7f105d5125a20c0a2` |
| `TextColor/Success` | `a87bd8ca0bcf3fa94b14d8948252712f1d7665a7` |
| `TextColor/Warning` | `1237fd1f686a74b069b0606dc9559bfaeda59054` |
| `TextColor/Error` | `25a08e0ea53240470bd1bc9bdbb487547e200800` |
| `TextColor/PrimaryLight` | `b93aeec51c45238c24e2286529f1a22486117904` |
| `TextColor/Secondary` | `bb8c725bd8586ae316b614e773f6e7869e6058f4` |

### IconColor
| Token | Key |
|---|---|
| `IconColor/Default` | `ff9190705952423d285a0b1be30a21a12b98bbee` |
| `IconColor/DefaultAlt` | `71075515d989ac785931a7f2a687f608c696df2a` |
| `IconColor/Placeholder` | `4e9c75f7fcc3908bd057320611a05f61582ddf7b` |
| `IconColor/Disable` | `645af7aebf2eee199c27014ff27531019632438d` |
| `IconColor/Primary` | `ed6315cd0b7569ce8af77f47874cced31f663b6b` |
| `IconColor/PrimaryHover` | `a9f3886d6c316397c97ccc1093d2e553fb95dd86` |
| `IconColor/PrimarySelected` | `fcc6583f79d5db55060720d4126d590ffed57d02` |
| `IconColor/Red` | `0b94df36cbd6b66b03a130d946ee424f9cd31bbe` |
| `IconColor/Green` | `a49946c7d8a682d078754ed938e432f128693008` |
| `IconColor/Orange` | `d656dc02ba67fe207b93da513aa6f15d3cd60a99` |
| `IconColor/Light` | `5aedd704c705ce35e92b31e1a7804f3d9a157dc7` |
| `IconColor/Secondary` | `a7eb7cf87810bb900c350e8573a9704b309b6af6` |

### StrokeColor
| Token | Key |
|---|---|
| `StrokeColor/Default` | `516696f49af6584db2280035f7e50bb38942baf4` |
| `StrokeColor/Subtle` | `672168994bd2237a9714fbde050c4ad14e7f61d2` |
| `StrokeColor/Disable` | `867bea593842cac4c265e3b32e8919fb9de46f3f` |
| `StrokeColor/Active` | `935a59588487b6f68170f7bb54b3ddac53807b60` |
| `StrokeColor/Success` | `02c3bf0816cd66e492843e30c20b354f1fbf8def` |
| `StrokeColor/Warning` | `3158e730e7140c11e3fc35aaa714629d9ece74dd` |
| `StrokeColor/Error` | `ff86359967192737708674e3101b7c1f891a7e24` |
| `StrokeColor/Light` | `f6b8c4ba1b85003d3bddd9187cb11dc9b85bbb1b` |

### BackgroundColor
| Token | Key |
|---|---|
| `BackgroundColor/Light` | `a9ad299d9bb41d9f8c949e558319413b79f717ba` |
| `BackgroundColor/LightGrey` | `0282b24b25bd83b850faf36b1035e716ea52e629` |
| `BackgroundColor/Disable` | `42b13bc79ae380465da698dddcb8cf81d632501f` |
| `BackgroundColor/Primary` | `55238fa215c59b72b175f659860382ea9b06b242` |
| `BackgroundColor/LightPrimary` | `68abe58a57284a58521073f12c56902116848a19` |
| `BackgroundColor/Dark` | `5016eba129ca3338ff279ff68f3c2644b585e79c` |
| `BackgroundColor/Green` | `697957a4d609b4e933a304666915d1aced25c1c6` |
| `BackgroundColor/LightGreen` | `b1e252020bc95011744baaafdc78c3ee6967d487` |
| `BackgroundColor/Orange` | `a62ed4e999ce286a62b3ca7fea79d9048f588e41` |
| `BackgroundColor/LightOrange` | `d4072ac15136201a8a5d30ed46731958310e9c7e` |
| `BackgroundColor/Red` | `6a420e02c40255a0c78b71e82d58c055744db09a` |
| `BackgroundColor/LightRed` | `0156c6e17e57dba10396eb803188ab2df0bb1389` |
| `BackgroundColor/Blue` | `4c87062ebb8b9f0e516d3d83de3d24f4c03e7135` |
| `BackgroundColor/LightBlue` | `f7a2ddad7b232d503d7361abde9a558c29aa8534` |
| `BackgroundColor/Secondary` | `eb70686936d154ec3215e39cf3ca0bd1d5ef8eb1` |
| `BackgroundColor/Hover` | `c31569df86b14a760f5aa6b0ec63dc07e2721315` |

---

## Size Variables — `figma.variables.importVariableByKeyAsync(key)`

Apply with:
```js
const sizeVar = await figma.variables.importVariableByKeyAsync("<key>");
figma.variables.setBoundVariable(node, 'paddingLeft', sizeVar);
// or use directly: node.paddingLeft = resolvedValue;
```

### Space (padding, gap, margin)
| Token | Key |
|---|---|
| `Space/0` | `4f203bcf4d2f5ae3cb6f54e0fa0008d0896c1472` |
| `Space/050` | `fd05b2aa12ef34671ed87e2ec9e4c6fe7e52cee3` |
| `Space/100` | `96b54e3ddb1e6b8f931ad5a6045d991d9c50b25b` |
| `Space/150` | `df2984f2b417f0665e31010522e097ad92afcb29` |
| `Space/200` | `cc56ab61c66d5fd418ca754e2398dc657e5a6d38` |
| `Space/300` | `617dee5801c847c905ab186f83d68d5456b55f99` |
| `Space/400` | `d441f2595b7a793fa3630df98959c394378e0499` |
| `Space/600` | `c709fb22c82987418edf782cb2104636ac91beea` |
| `Space/800` | `d63a8255fb4bd51c25df010badddcef5f6183251` |
| `Space/1200` | `dadc84b4a2c2d5fc8a38bc5f63f0944074bac3d8` |
| `Space/1600` | `f2a4f6c23f04073127241b03c8b216efd29769a0` |

### Radius (border radius)
| Token | Key |
|---|---|
| `Radius/050` | `66478d13fb03a83f0c6abd2b3fb267c394fb1156` |
| `Radius/100` | `8a63307eee34ca3b64d7894185696ba7b71e6e6e` |
| `Radius/150` | `b5442e448e8eb1b9198ca1ef3b0246283fea58ef` |
| `Radius/200` | `cc44c88859991fc10452d61aa5cd6e95f42cd48f` |
| `Radius/300` | `5e639289399028b128033d05910538f3a4534b50` |
| `Radius/400` | `916f23e7dab5b5eb38637eebe56fffd820629e83` |
| `Radius/Full` | `439c887a774cdbb8813a8715071c95c580404a27` |

### Icon Size
| Token | Key |
|---|---|
| `Icon/Tiny` | `6d8d537d660045ab7cccc67bbd4d927654475e7d` |
| `Icon/XSmall` | `1119b30cb41ca207aa435a0fd2abbefc09afe310` |
| `Icon/Small` | `39b216a48ad0a12320487f8a4765b070dce793c0` |
| `Icon/Medium` | `30a2d995e2cb20287b8f85ccfdc16f5f9af593fd` |
| `Icon/Large` | `1aaef393c6779d1b0152938e7ef7d191586f5766` |
| `Icon/XLarge` | `d1f2e4c130445e627cb56b0fcc6d3fab9dd96da6` |

---

## Text Style Keys — `figma.importStyleByKeyAsync(key)` → `node.textStyleId`

| Token | Key |
|---|---|
| `Headline/Large` | `2cb1062fb19512914812d1d6ad21ec26e716a8dd` |
| `Headline/Default` | `b9374816ae643d93ec2222affa5d365fd8a89c7f` |
| `Headline/Small` | `c9cd967da32cbbe25137a530d92d4e6c554f856a` |
| `Headline/Tiny` | `225da8f6c90c922cd911a50802b524a3f84f5530` |
| `Body/Large` | `45fc2659958dc6e3ec1cb8a75fbab3991c26ecf6` |
| `Body/Large-Bold` | `05400eb54f24fc465d7e20bf9f7cfe9ef810438b` |
| `Body/Default` | `60a662ee7879c69ce7677cb75a04a30f38516e16` |
| `Body/Default-Bold` | `366e5eba1da4c1b181e7ff4666314d6122bc9a0c` |
| `Body/Small` | `b54cd49b4ff4b9d068c4bb9e99cf7a4fb82e7449` |
| `Body/Small-Bold` | `2551b0afe07d61fe814ddf5268e4b086d410738e` |
| `Body/Tiny` | `f62ba2183d1b5a21ef6a7b174ff1311904a1374c` |
| `Body/Tiny-Bold` | `db1113a4c99468c18bef4e95dea52c0dc6cf2cb6` |
| `Paragraph/Large` | `8d71cbf3f0e7560f19a1c4f90a67c392c29c8c8c` |
| `Paragraph/Default` | `90f1d4db403725f70a3d645f18b32a5014dd1c72` |
| `Paragraph/Small` | `027e91dec3a373c3e52d2fc58985eb21fd71a8dd` |
| `Paragraph/Tiny` | `ef2658f1422a54f6e5f87618967905d415c60d0e` |
| `Caption/Default` | `7fd9309e6e25a541426508c461d67095140a0efe` |
| `Caption/Small` | `39c25455ceeebc778038951237c5f88f3385f948` |
| `Caption/Tiny` | `a546dc645450d306865fa2eb57187ccbbffae151` |
| `Caption/Tiny-Bold` | `000d783d517ed5f45be5ee2d1d90f5f2d48ed4da` |

---

## Component Keys — `figma.importComponentByKeyAsync(key)`
File: `LD5Y3L9vAvw3MAU2POgseI`

### Qty-Editor
> Komponen quantity editor — digunakan di product card dan PDP.
> Berbeda dari Button. Source: node `1708:4375`

| Variant | Key |
|---|---|
| Size=Large, State=Enabled | `1bd2b1db1092117b2884daa2ccec75f8fb73419e` |
| Size=Large, State=Disabled | `7b8ce92fea71ae0664969b1d9e2ef935db55ec3c` |
| Size=Small, State=Enabled | `9215f1c99815bbcc74c8e27cf1d6c2b687282e5b` |
| Size=Small, State=Disabled | `9effa98eb66c02657416b79a96ad6070be7747df` |

### Checkbox
| Variant | Key |
|---|---|
| Unselected, Enabled | `b7c5042702731d36a9d59ccf78d9463509d90831` |
| Selected, Enabled | `84787943d2a0696e2f05b2db2b3936b6e80c7878` |
| Indeterminate, Enabled | `c7223348e95eb7b0de3b36f36ae3bff7a3e39aaa` |
| Indeterminate, Disabled | `429240976733a90803a6396e003baa360dd9f969` |
| Selected, Disabled | `9184f980f0e6f015aeb666cad6e2d2edad2e438c` |
| Unselected, Disabled | `193487bec1f1e23f7def87b9107a5b9cff5016a3` |

### Chips
| Variant | Key |
|---|---|
| Text, Not Selected | `8096257ce5f92dd47e474927a8ee485d8299e0eb` |
| Text, Selected | `398436432e378a69f30f8a3c2a9ee65a3fed42db` |
| Icon, Not Selected | `2bbe7ff1a58aa432a85308a9d534fcf8ffecd0c8` |
| Icon, Selected | `ef97ca4b5a8a7144c95143a3b7f976600d96afc5` |

### Divider
| Variant | Key |
|---|---|
| 1px | `aca785ebe3e264f8241f68b529833a7c4b41d84b` |
| 2px | `7f71196b307728bc9a37787879d9aab787122421` |
| 8px | `15a30c00f6096ab9ee291997caef73ea422f5ab3` |

### Navigation
| Variant | Key |
|---|---|
| Active=Home | `8cbbcc09739fbfb857b58e13bcc0026ce1905fcf` |
| Active=Promo | `38bee517905bb9f3ff049f0a4f282fcdcb9b6e46` |
| Active=Cart | `16d468c409dcc9e0c2389c3d397042611d5b5ba0` |
| Active=Order | `ba17d5b88f6b6b1cee5df8d2394e1006ebd67270` |
| Active=Profile | `7ebac6b9d5b922cd0f5566b8ea99829ffe054dec` |

### Avatar
| Variant | Key |
|---|---|
| Size=16, Photo | `1af8336318fa024fea9c3e70ce0ad6104f5dfb4b` |
| Size=16, Placeholder | `fb01e483654c6c1b3a722d8d0e8d344da0c3019c` |
| Size=24, Photo | `866dea9338a291b66ba1c4c2046bcee8020a7c38` |
| Size=24, Placeholder | `4afbba3d56ea1590410289ccf8884575b74c41d0` |
| Size=24, Text | `bc35b9a26baee3390b65e1954c7d60bf406d9ba4` |
| Size=32, Photo | `cbb8c2db9d10882b1b535d61a6d765ddd847608d` |
| Size=32, Placeholder | `fd31eccce0b08e03aa6d453d3f4420e287afc107` |
| Size=32, Text | `2ee1c247b9ded3728facba5698271b4147e50a77` |
| Size=40, Photo | `15d5f05f2824941bd3dced150acb1636a5943747` |
| Size=40, Placeholder | `2309a989065f8699991b43ea9627e1a17284b3b7` |
| Size=40, Text | `828d93e8c108f50ca878706cb782aa8e42cd706e` |
| Size=48, Photo | `06e20c016249957bf75b7dbd2ee6e24470c2b696` |
| Size=48, Placeholder | `92ba73a263782c10f64bce2287c40cd819c54d5e` |
| Size=48, Text | `455e991e5d0703bcb012b06faba831520b409407` |
| Size=96, Photo | `4470fba27e270952c52d88ba995c04142837afbf` |
| Size=96, Placeholder | `d53d8f37f7fa276fbdb278783e9827b203bd2ec3` |
| Size=96, Text | `a9e354cbaeb9a78f288e297e681d962c64c08e8a` |
| Size=128, Photo | `d629bf48bcd037d1460704e11bb9927298652166` |
| Size=128, Placeholder | `ec1b277a97b841408e289389d2300b1f20ed6186` |
| Size=128, Text | `f6af3ec05e1c22456332d313f9f4710df3603553` |

### Alert
| Variant | Key |
|---|---|
| General | `1ecb1be3e870b8f468c2949abb43a151376d63c8` |
| Warning | `8e5c1d2a2c0e2dd545751938a8fc9bb93dbb0133` |
| Error | `05f10832168661ea87a9a1ce16c0b9a05f3f2197` |

### Label
| Variant | Key |
|---|---|
| Small, Green, Not Filled | `17552a24e717d462dbf32e9e44cb904ad483ac76` |
| Small, Green, Filled | `d3a41981f4c6d0d783907995ae508c87526732c1` |
| Small, RedDark, Not Filled | `3c83c0bf1b67af2a94feab3b77dad882dd7567e4` |
| Small, RedDark, Filled | `2a3fd9437176e75a70233e64a43fcaeb29115b43` |
| Small, RedSoft, Not Filled | `dcc452e6fb7295d9c3b34f347e1a9408b510e31e` |
| Small, RedSoft, Filled | `11dac1e54bd549ad8b7bb4519dcb5952e707a308` |
| Small, Orange, Not Filled | `8512243194af7d432bc447be8a298da0aca12833` |
| Small, Orange, Filled | `d7d8322f725f7f3356fb95863ac3b06e256eb6d7` |
| Small, Blue, Not Filled | `50ef52e4d7bd6e1e1c5b19c1bef3e5cc734eab67` |
| Small, Blue, Filled | `e8e57ffbdff4b56e49daf8df5af577753d115083` |
| Small, Grey, Not Filled | `7c5782622701b3c8e08d13fbf0995eb9c2d71204` |
| Small, Grey, Filled | `8583093f57482b267c3847b9ef622763271529fe` |
| Small, Purple, Not Filled | `01dd9717cd048798ca70f94d9910717a859745c3` |
| Small, Purple, Filled | `34bf772f7e5d9835f155e5c34aa293668558b65a` |
| Small, Magenta, Not Filled | `a13705a50d12dc281557f35ca047d4c9b30641ac` |
| Small, Magenta, Filled | `2153849f7cb371fc697b77d637d4cca00af1e83a` |
| Tiny, Green, Not Filled | `2c536dc03783708cf22c3b01b88d628d3c5fea24` |
| Tiny, Green, Filled | `042500ed86ea4487571219d52306944df8cffdbb` |
| Tiny, RedDark, Not Filled | `89fc86c5c3ce43516fd55462e8c1a9f1c02ed898` |
| Tiny, RedDark, Filled | `979663e72fd3b523290af965ce318fe53a2d4250` |
| Tiny, RedSoft, Not Filled | `a2a69f350cb1c52854da3945dfc8ff2e0f9167e5` |
| Tiny, RedSoft, Filled | `d327feb185e5c9987fe9eaa1c902ba2094ca64d1` |
| Tiny, Orange, Not Filled | `1e723ea1c5dd3455ad55e8bb16fd724c9b7d11b2` |
| Tiny, Orange, Filled | `74f25294837bda83c842da8d43541829622c46d3` |
| Tiny, Blue, Not Filled | `961ce758f7ce54683487f2051dd5fc9dbcad3423` |
| Tiny, Blue, Filled | `af7219be49e60216da8a0217671886c8b2a3db94` |
| Tiny, Grey, Not Filled | `9c60c126bc0300326adf1a20e30d1c78dba8a48a` |
| Tiny, Grey, Filled | `fab4ad035e4e835a454d69d53256f3959ca8085d` |
| Tiny, Purple, Not Filled | `ea70afaa15fc07478ac217d61eb047d290f98a09` |
| Tiny, Purple, Filled | `080dc14dd46bd9526a6c376d72e35e490680911b` |
| Tiny, Magenta, Not Filled | `a642caca1dda29b0445802345dffc9dd78a8df57` |
| Tiny, Magenta, Filled | `adf4cce32151a5c82a92216598505ee863727287` |

### Carousel Indicator
| Variant | Key |
|---|---|
| On Colored Bg, 2 dots | `51e33297860aea07a8d9ded21cc8a590173e4077` |
| On White Bg, 2 dots | `ae010eac2aa234f0d0007872a33750a19eeeac62` |
| On Colored Bg, 3 dots | `54d61d964f2b1fe056fe73e4a6efcc1ece4b222c` |
| On White Bg, 3 dots | `b651f3e290dccb555b841e64228c05302f99c0ce` |
| On Colored Bg, 4 dots | `2b3d3f70e1ab06f8e9bb73075402b7170a45f60d` |
| On White Bg, 4 dots | `3f335756086981e7cf8f40972168f595546c8183` |
| On Colored Bg, 5 dots | `d8211431442c9bc8f5bdbb256fa3185f74979a20` |
| On White Bg, 5 dots | `aaf1b5e3ef02681f479636112bd5695b598dd00f` |
| On Colored Bg, >6 dots | `2609e142b62c72f5ef0891f029d39f557f1d873f` |
| On White Bg, >6 dots | `5c4a0b90a372c43c57e06f100d2a0023d6f8e6a2` |

### Countdown
| Variant | Key |
|---|---|
| Dark Red | `bb702c6603347177e114b914a3d523186eac484b` |
| Red | `5ed8446553dbd396a5ea1bad1a1b7beabcf77f2d` |
| Orange | `ae2fb78bbdc4e98635223667156252cb23eed09f` |

### Date Picker
| Variant | Key |
|---|---|
| Android | `df0a5f1f1659cfe5be1800d2da96062a7376738c` |
| iOS | `34ac36193f9522ae1f80d682b959405f6a64618f` |

### TextField
| Variant | Key |
|---|---|
| State=Enabled | `301e5b071d0fab0e9058a0f75381b7b17426e330` |
| State=Focus | `9a56f00c694d6be561588ad07823ecb0e5915e6d` |
| State=Filled | `63b1111cd363ec382724473047d0f3b8bdbf99fc` |
| State=Error | `2c52e7e2cc9ad51caee2fe253c032c9a39adc80c` |
| State=Disabled | `f00c79c8fe1eb5ba7711db248f5ddda2019d4b5a` |

### Text Area
| Variant | Key |
|---|---|
| Expandable, Enabled | `b3945ab0cae5f643dc3bf5e96dda3b5c80d6b7fd` |
| Expandable, Filled | `a7922d6574b8d31d226fdc52c17b40158adc31c2` |
| Expandable, Focus | `866eeca91834abc252eeebee70d054341ab28dbb` |
| Expandable, Error | `f8b9724c25bfc1e39587c564fb26382d29bc6106` |
| Expandable, Disabled | `f7fc955b8873fa8716507058cf9daca6187f7ba9` |
| Fixed, Enabled | `bd97bd7dff2a74ea5756209fb5de0e71a1e36bf2` |
| Fixed, Filled | `471ca4e10f214e73da0814335bb2d5f2246e716c` |
| Fixed, Focus | `55f6136366f5ceafb88a6512664588f0580bbc98` |
| Fixed, Error | `85706023af655a978ebe889408ebd0502b4e039b` |
| Fixed, Disabled | `e558f96ead7a72b2ef0b81cce7a9afccfc7c796c` |

### Searchbox
| Variant | Key |
|---|---|
| State=Enabled | `6e33ce9316027c1addb3aca9491640cc094eb610` |
| State=Focus | `4c6894cd3c3b5901b302d286ed8c762f04110455` |
| State=Filled | `49d9a452331fa41a359881b7f594aa0bd941cc70` |
| State=Error | `e7b6bf02b3b9541efdc8e823cb3a0068ef76fe87` |
| State=Disabled | `032334b848cb782bb977952fd995b6e647fc7df4` |

### Toggle
| Variant | Key |
|---|---|
| Active=True, Enabled | `7b57832d6fa52045aef01f1af8ec8e19efc11e35` |
| Active=True, Disabled | `fba9b66d29a716eb657b240a0ff8a2a2871c809f` |
| Active=False, Enabled | `18dc6c1b97d914e6b55a4fcf5b4263f4e1969566` |
| Active=False, Disabled | `ce000b75dd27af9463a638188bbf6c56561ff361` |

### Radio Button
| Variant | Key |
|---|---|
| Selected, Enabled | `a620898e9192a9ac26c296229a7e33115870c449` |
| Unselected, Enabled | `00747c5a02ef869607ef8cd6b595b8b0dfb3527c` |
| Selected, Disabled | `42a2827807b1d3dbe0ebcecf954a9bedadb61cd5` |
| Unselected, Disabled | `ec58ff8e918af46f2b0396de7e2c5cf001b00eaa` |

### Tabs
| Variant | Key |
|---|---|
| 2 Tabs | `9663bf896eb51dac36c38a5612df652ff81aabce` |
| 3 Tabs | `f6b0ab9f8fe0eba741eb21d157ca0cbd6d9b51eb` |
| 4 Tabs | `66080e74a34f51086b7120e3460fe5674e3fd422` |
| 5 Tabs | `ed0eaf94bf9e9434b1735bb3d2fce386fe3518fd` |

### Bottom Sheet
| Variant | Key |
|---|---|
| Type=Handle | `3e2c80ce6070a1e8dd8e38b37318bfcce93b9b56` |
| Type=Close Btn | `ee5d34a34ea157c927317461184b98f08988a07f` |

### Snackbars
| Variant | Key |
|---|---|
| Default | `a832e42e2cf1a1b4b579dfe76b093d5e86e2a7d5` |
| Error | `ae812cf344f0bc3bf5e957b30d4adb08348c3104` |
| Success | `ce71aabc840dfb2efd3b32e636addc1fda463c0a` |

### Notification (Hint)
| Variant | Key |
|---|---|
| Small, Red, No Number | `caa138b3c335521016f27a7d3e9ad16cd8faa6ee` |
| Medium, Red, No Number | `cf2daf45db75fc3ec83389f4540c6417ea16ac96` |
| Small, Blue, No Number | `525e61ed0a2637de6569d29fd583677e2cd7e0c7` |
| Small, Blue, Disabled, No Number | `6d1e371e21b456f488f7fe38986c72e44e5320e5` |
| Medium, Blue, No Number | `96c5ec375d50c4ed1867034e1cd33aac05f75b03` |
| Medium, Blue, Disabled, No Number | `c59b537068a934595d324752f1cb55f6e6da0530` |
| Small, Red, With Number | `c0016d32801025068efabd6b7cb72fb2ead36ad9` |
| Medium, Red, With Number | `932ad8a0c0fee4b19b64b087825c8c99c726dab0` |
| Small, Blue, With Number | `98ed822cb6943674881be340e6c431531f233bb3` |
| Small, Red, Disabled, With Number | `6b65b672e9c8fc731d98893eb6eaca76143e1f30` |
| Medium, Blue, With Number | `1948fd1ae04d382f5912a16209f67f692732a420` |
| Medium, Blue, Disabled, With Number | `e69be22a9146e2d6bde431f9d86088b901f5b93a` |

### Progress Bar
| Variant | Key |
|---|---|
| 0%, No Label | `25f53dffcf4908851d3b07d44df20df48896fc83` |
| 10%, No Label | `4bfaf3e22b2234207aa4fb5b97a9ef9a2420de2b` |
| 20%, No Label | `acb1bffe63ee791779047fbb9fb3135288c8df6d` |
| 30%, No Label | `1dcd00b058ef2ce93780f677c933a64067540b59` |
| 40%, No Label | `0f3ce034a6f102405f9a7edfcd21bd9f6e9d74c9` |
| 50%, No Label | `465ccfc9b5b400bd69d5ba91d3979fc83ca77a48` |
| 60%, No Label | `a5b0da1aa4b34c054700de98adea0c76d918d3b8` |
| 70%, No Label | `10f257ca356177a7907993ae66d65dbc012a988a` |
| 80%, No Label | `ddf935dd84536c20e6444b5e88dce8a4246e10f2` |
| 90%, No Label | `8b3e977296ec53e8d09fc7f375b1f3f85513d27a` |
| 100%, No Label | `c06a55cddc5979a1b2a166d94c23bc2b68b3b177` |
| 0%, With Label | `88de6a852609f7b584a7599ce60f394c421deeb9` |
| 10%, With Label | `d40171aefa71f42fd84c742f0ba2e38f37f187ef` |
| 20%, With Label | `08d078f7faa702eb7305ecaf3122700fd7b8eb55` |
| 30%, With Label | `692affeab1d497b700e9b898823accab520754f5` |
| 40%, With Label | `1ee6794a999c9f0bcc2caa7af57119322d336358` |
| 50%, With Label | `3e16b7bc870691bb5c8ba09e41395defac465f0d` |
| 60%, With Label | `85bae38b4c6908263975047c1acc31179fa2315f` |
| 70%, With Label | `b60269c590d5366b3778a234635744ad922ae661` |
| 80%, With Label | `3021800b427ccced79a287eb181966725d8cd850` |
| 90%, With Label | `c389ab9658a15fb8d6a4611b47ae7ea31ff6a7bf` |
| 100%, With Label | `ed567d63bcc5cf3d800da69efb267e27f6297124` |

### Tooltip
| Variant | Key |
|---|---|
| Default, Arrow Bot Right | `4a0261b9d518b7e61910f058edaa07efd917ca98` |
| Default, Arrow Bot Center | `d8844ff280ad9a9aa9618a16bb9904e4aa1c8511` |
| Default, Arrow Bot Left | `ec6609f225596c8bd3f7b375728d3a36546335fa` |
| Default, Arrow Top Left | `3b3f0f417e082da1c0b42dc5156d8ef29694a11c` |
| Default, Arrow Top Center | `cf0afaf50ed0b6f6a7492508e543609f0fee0a9a` |
| Default, Arrow Top Right | `11f5460b29341c66356efc31b1cb78b407d03f90` |
| Leading Icon, Arrow Bot Right | `32bfeb324612db3a56384599accf749a239095fa` |
| Leading Icon, Arrow Bot Center | `bd4a1131a8780fd90562b239d2eced7a6743a1a0` |
| Leading Icon, Arrow Bot Left | `153300074252a5f648675911d258f414e144e15e` |
| Leading Icon, Arrow Top Left | `359c435d0195ed9c89dfa98805513d08411b8946` |
| Leading Icon, Arrow Top Center | `dea534b4f6d6e97f2181fdc6b4d08a3bec21f48e` |
| Leading Icon, Arrow Top Right | `0c6e1df614d596dae302d9ffd37faeff0359986b` |
| Close Button, Arrow Bot Right | `bfa0b2857ddbd41abdfc4eb4fdb5a266508efd92` |
| Close Button, Arrow Bot Center | `3c225865d2d727b5bb8247ec212a3b962dd0b3d1` |
| Close Button, Arrow Bot Left | `28f44cbc4f27373dca0948f4cea4e23b1a903bf3` |
| Close Button, Arrow Top Left | `9230c2cf34a374242831af7eb721fb5c8f49f8a3` |
| Close Button, Arrow Top Center | `3f2b6b11fa27760d0ae4e513d4d152b06f1b3333` |
| Close Button, Arrow Top Right | `f8b34f7d7f1f70a30802fe53e343af5c815778de` |

### Button
> Komponen button standar — Primary, Secondary, Tertiary. Source: node `1680:9053`
> Berbeda dari Qty-Editor. Untuk quantity control di product card/PDP, gunakan section Qty-Editor di atas.
| Variant | Key |
|---|---|
| Primary, Large, Enabled | `d0dfa564d68275c6b4db1f692ec8a344109cc6c7` |
| Primary, Large, Pressed | `be22d8f24756b07e2824ec74002ecf237309cc88` |
| Primary, Large, Disabled | `f18e28dbfcca32ddef82694584061d1d44d1277c` |
| Primary, Medium, Enabled | `80bb4cb7f021af1ebaf57f0a897ad61a7963f6da` |
| Primary, Medium, Pressed | `726db69c09a1a60bffac0056dbf575070e193898` |
| Primary, Medium, Disabled | `abd462d68907e9b636d92f9821e78b105065b90c` |
| Primary, Small, Enabled | `36619ed02eae61a1be913feb151582dcec953f16` |
| Primary, Small, Pressed | `af6814bfb684cd44bba25f4e23e609ac09aec3e7` |
| Primary, Small, Disabled | `8f022103b26a14ef1b36fe380144a856143c883b` |
| Primary, XSmall, Enabled | `b85ec4a420e294dcc3bb9160c9e97265d414869d` |
| Primary, XSmall, Pressed | `2382df29bfcfb6fa3a49943172bd9d4674299ce9` |
| Primary, XSmall, Disabled | `60848ae884d66c8a86bd8fe45a44d4667a788f01` |
| Primary, Tiny, Enabled | `f1696419f62adafd2acaddaa51d362c3a9906fb8` |
| Primary, Tiny, Disabled | `18d979f333d726be6c78ffef5e8f4766ddace0ed` |
| Secondary, Large, Enabled | `e0fdcbdb170449020e9e32af77a521c10090cbfa` |
| Secondary, Large, Pressed | `9e51d79b0ed9d1350cee658e6f8aa743c0f81f95` |
| Secondary, Large, Disabled | `3b35312e708aba04f190ca9950d1f6a80ab66705` |
| Secondary, Medium, Enabled | `7fed3b8ebe56589b086e191b1e6ba95f54df884e` |
| Secondary, Small, Enabled | `0bb3448e8bea51ab3ee52030763ee5de231c4501` |
| Secondary, XSmall, Enabled | `f4eaaae28e63ff5389cc3e14e299933c4f3edc74` |
| Secondary, Tiny, Enabled | `7078e29edcc2dbc5c3bfd2466f62cc7b7b0b2366` |
| Tertiary, Large, Enabled | `1f8515c023c1de98d85d1f68924e1881d5539889` |
| Tertiary, Large, Pressed | `17538fac91c1fefecc73473a94ba7d1e99368494` |
| Tertiary, Large, Disabled | `78d9c3079f25fa67708fc1e2d075ed8a7d0c4761` |
| Tertiary, Medium, Enabled | `3632a09f273e27798b52480168d00409b38490cd` |
| Tertiary, Small, Enabled | `d11a3b3308b8ffefc1a237c49fe417f995739ac0` |
| Tertiary, XSmall, Enabled | `d684d1b2b1ceef291f70e0c09bb4f1644eeabdb2` |
| Tertiary, Tiny, Enabled | `a0db1db1d93f111c477daa82aba9d83a21fe52bf` |

### StatusBar
> Component set ID: `1765:3240` | Key set: `39391eef0fa07451a3f306bfb4ad30f974e52be1`
> Sekarang published — import langsung via variant key di bawah.

| Variant | Key |
|---|---|
| Platform=iOS | `fcdfd90fc22eaa4517c39afed4725c0deba8021e` |
| Platform=Android | `e9942d7723a44a8953beb0c6c70f4a3de2c3833d` |

> **Ukuran:** iOS = 360×44px | Android = 360×52px
> **Fill:** `BackgroundColor/Light`
> **Fallback** jika import gagal: buat frame manual ukuran + fill di atas.

### Header
> Component set ID: `1780:22792` | Key set: `e1d20c667e2d9d2dd82bf2a365dd59df3a643c80`
> Sekarang published — import langsung via variant key di bawah.

| Variant | Key |
|---|---|
| Type=Title | `b3504d7ec39c68f3941e6b3584213f20a189e091` |
| Type=SearchBox | `5610128275e670a38cb78d416fb553b4ed703531` |

> **Ukuran:** Title = 360×48px | SearchBox = 360×56px
> **Fill:** `BackgroundColor/Light`
> **Catatan:** Halaman Home & Profile tidak menggunakan Header — pakai custom header.
> **Fallback** jika import gagal: buat frame manual ukuran + fill di atas.

### Top Bar
> Komponen yang membungkus Status Bar + Header sekaligus.
> Gunakan Status Bar & Header secara terpisah untuk fleksibilitas lebih baik.
> Bisa di-import jika dibutuhkan sebagai satu unit utuh.

| Variant | Key |
|---|---|
| Top Bar (complete) | `e170871cfe859b484208877a0aa6da675759884b` |

### Dialog
| Variant | Key |
|---|---|
| Dialog | `b96500b73dcc70b14bd4d9fd0be0b69cddd46fc9` |
| Content Dialog | `d61245f6057a5036850219cb3371f6f9d0823fc0` |

### Overlay
| Variant | Key |
|---|---|
| Opacity=50% | `b95bbc060a6c03d4e38b6bca6c6559cd10342964` |
| Opacity=30% | `34ffd5bdc2f7123905eb12c3adb5feab01bc1734` |

### Status Bar
| Variant | Key |
|---|---|
| iOS | `fcdfd90fc22eaa4517c39afed4725c0deba8021e` |
| Android | `e9942d7723a44a8953beb0c6c70f4a3de2c3833d` |

### Time Picker
| Variant | Key |
|---|---|
| iOS | `e870395be8d226e7957008e7b4ee85785bc59086` |
| Android | `10e306be414a0fa54e71ffee535bd34d8f075e55` |

### Keyboard
| Variant | Key |
|---|---|
| iOS, Default | `e3185ddf93f9e9c46951eb82d83c7c1077aec052` |
| iOS, Numerals | `36095b6f28b515030fa350df269e9920c757d8b1` |
| Android, Default | `4224d2e6c7d1f9645e89292477b4b0bda97a445e` |
| Android, Numerals | `e3a09b7074188c09dd8e202d244706da21d7c45b` |

---

## System Icon Keys — `figma.importComponentByKeyAsync(key)`
File: `LD5Y3L9vAvw3MAU2POgseI` | Page: "🎨 Icons"
Default variant: `System=Outline` | Size: 24×24

| Icon | Outline Key | Filled Key |
|---|---|---|
| icSearch | `439d5f60df820d35077553903528c346d9388c39` | `cf9f8efcd5c59745e295271c9ace65b87ae57189` |
| icHome | `498673b8fc17f0cf531402cd7f943bb5961b30ce` | `374d691c051d719b729e401013b0000f3d14675b` |
| icCart | `48e80bf7082c0b6f8f6994c25928a5094946f09c` | `20a2bde6cc84e08d32b5a14dfe9443e2999a3bbb` |
| icAccount | `e764dbf6a1ea22b90b8ed38dd1d42dfd1d0c5799` | `d4725243376e3cbe4982f2854a056f188e9cae72` |
| icHistory | `25f07c2c85e7c68debec05a858936a7510d8e307` | `02cdf2ccd8d14ac0c3af22d7e764f26dadef9e62` |
| icBack | `990874f942be3fa7ca54594caba1ec72b1d59a31` | `3372e602921f362ecdc77d4080e8c82e49f888d8` |
| icClose | `c979815e0371ef9b72216eba9e462ccfd8ccf766` | `ad427d7b1cf09a583eb6db6991dbd0a3bac917bc` |
| icChevronRight | `dd14d0a6bc38fa8cac02660e8c82a476bb8a5723` | `03c34500384ae0b66d4cca57ea3d1feb804972ea` |
| icChevronLeft | `bf8aa62d15c0c176718e86d9cba8e05df3592e8d` | `f2c1bafada9d66abf50b9c356d89376200e5514b` |
| icChevronDown | `a5e57ed73253dad0c30d878fbbed5221f37f6ac0` | `1058629692ccfc39314827d123585d83b716f421` |
| icChevronUp | `38df8f85a6e3ac48b90bde7a88f97d1b84e2829c` | `d17b836bc598529c349c62b43524f46eb1176fef` |
| icFilter | `2e604e38ecd0b0c523b56e8ff54e8628c15532d8` | `b5051ee06187169f3e7745df0f40e253a4fee5d0` |
| icSort | `1eeb842ad4818a52ab554a59d5f428f31ae54961` | `b1d320a9e4b18170fa505e041e26f3ee7de66383` |
| icEdit | `b99897fb5bf49357ecad5d5ae04d89e715c240fc` | `2867f55098bab01a92a007ac5dd4c25522354a31` |
| icDelete | `c6ef36768bc4942a8219e836678b267777f189fe` | `ad0300637f58c3a188441afbdb989c1973261b92` |
| icFavorite | `2f87b0776893e757fa716a8d09ef3c9089183dd7` | `f9470e9a8ddd8d0ef30f88ea7701746e1adeca72` |
| icRating | `b7acc486e5a246142944b62f63dd0aea08fbf584` | `8611810fbf85db80a6b3345e3b93900cc17e52f3` |
| icCorrect | `d9a2b366ea4c02e9cbc74fb302e6fe5fef4449ca` | `e5ebf6a67c83a5544b1cf126863425da43eda8ad` |
| icCheck | `8456dac81560decc3eeffa58766b20d24559d4ce` | `1684162e3faadb23997337de1db87f59dddf869e` |
| icInformation | `0894a4ac70225b96036f2e67e765db28a42e16f7` | `5642fba22ee25f0d176b74e0e066e1e20bbc1b67` |
| icSetting | `1d6f0e959bfedf5a62a06de1f7fe1824d221a5b0` | `c87f2b5bef317619a5c3183515aa1fe030dd85b6` |
| icRefresh | `ff991e807f484bad24ab4b9f3c645a4edc25fff4` | `320730213aa0c24d7c51b65d7f09916f3b3fe6f3` |
| icScan | `b4ebf066fa4b4dc7f8a0bc1afacc6721bf43b3e9` | `d73c2b4945b475ed72e65569b18448c1eee870dd` |
| icQR | `0e4e8077ec5f394369cd4ffc748c5838bda9cb5d` | `48859e608d00435ac02f50dde82a0a66f4bef648` |
| icCalendar | `ffbabcffa0bf0b36f612d0c77abb6bd8985cccc8` | `b177b7f16048510a820be87eb09b5caa030c4999` |
| icPlus | `bcab04626ccfe3b408896fb7c706b128d0bde3be` | `78394e71b016fac2424c9ec84b9e45cd7b28e1c9` |
| icMinus | `fbb56d7ceafd5d25b3486803463eb6f6e2f69567` | `6956fa02f07f3bfbd16526f9e2850592c913ceda` |
| icPlusCircle | `f9bb757b03997d8cc57b4e526cb56d0f9254084a` | `306c833ca99e71b92e64d87286960a706e8a1a2e` |
| icMinusCircle | `628042131635e5867c28d20c5ff539ad9a2c651e` | `718400d02be8619be6ea4782c76f90aa4df806e3` |
| icList | `c0b9ffa95578232d9307e721c8aa43c8b37e36c3` | `6c45ac91facb55ba4c7b0dfaa7433c9255ce89a7` |
| icCopy | `88a9126be25b2a94adf6cc842e51a5d53fbfd086` | `590d13006e46169f3a777db3a5408aeefab09c2f` |
| icShare | *(search in DS)* | *(search in DS)* |
| icGift | `94c7beeeee7af1362c9bf5636ecac74cdc602eb1` | `95727d53c26dcd333a4d2d5a2ebbe5faf40b104e` |
| icBookmark | `4106a469a1150eb9516a8338746bf8f9f742173b` | `78a37c9d6e37f04704ef54bdf164185ee3eefcde` |
| icMessage | `b38e13c7107b78cf07c001ac823cc715a9cef5a1` | `7678f1c9bbe7d067a6009659137c570ee3f8e1d3` |
| icChat | `931a653f3f5e094f886ebb893f461046c52fdc96` | `0cfeeb26b92a137b19106c390732b9abaea3fe75` |
| icCall | `89b2c146971bb003551f317b4e8da34b24543530` | `ce726e894948e5a2040cd0211568b685a55478ce` |
| icNotification (Hint) | `cf2daf45db75fc3ec83389f4540c6417ea16ac96` | *(see Notification component)* |
| icAstroKoin | `6c74035d21f2574766b0ac572ca68ba555872a44` | `dfdde40724681517e051ce9d1e7f041839274fd1` |
| icKategori | `4665920073b5d5c99410e0481a66f6ee3e84868c` | `ae00d64343383642055ae1647437c96bcb8ade97` |
| icLogin | `72a99b99c33e25292baa4508cc32756899b80ca5` | `d8bf4389b3d550a50971b469af5e082d734bb667` |
| icLogout | `2d8356d872178f857f554d2e51f34f0e758664e4` | `7bd47d77e7646f64ad1aa5ac092be712bf9a6f25` |
| icDashboard | `6a39464409425fbcb837700857519a2a7aad3ea1` | `f258985c5ece5596617e71e6291b211f63e3c310` |
| icSee | `41c116275ad5441b33fb03e90123e33eccd64e3e` | `035f8076abc879243d73aa418dc74f4dfcb82fb6` |
| icHide | `b6ab74dde3195b26bc37330a6b7cd666cca58be4` | `dc5c92a65d3a1b8f86515661a3d938706861313a` |
| icAI | `d92508edd56d4f917796e23d40d936afe506d9fb` | `e7eaf58da7b863e46525fa9a807edb16aef85d20` |
| icCustomerService | `4b3d2834f4ebfaad6d016cedbf53d6b3844e9e4b` | `714bff3c1e5f276f8a492cf1cf7362105d4bd525` |
| icQuestion | `1ee3069536d7a7a4011c66895acd9d6b1f665458` | `19d86d1051f8ca8cca6970e72f8fd830817e2a71` |
| icForbidden | `1a025e2ef1ae9ffaa12d6cf1816de2f2b114cbe9` | `b0f0a4e2914b7232cf654f85ae33f7d71cf4584a` |

> **Icon key not listed?** Search in Astro Mobile Buyer DS file `LD5Y3L9vAvw3MAU2POgseI`, page "🎨 Icons":
> ```js
> const comps = figma.root.findAllWithCriteria({ types: ["COMPONENT"] });
> const page = figma.root.children.find(p => p.name === "🎨 Icons");
> return JSON.stringify(comps.filter(c => {
>   const parentName = c.parent?.name?.toLowerCase() || '';
>   return parentName.includes("YOUR_ICON_NAME") && c.name.includes("Outline");
> }).map(c => ({ name: c.parent?.name, key: c.key })));
> ```

> **Component key not listed?** Search in Components page of `LD5Y3L9vAvw3MAU2POgseI`:
> ```js
> const comps = figma.root.findAllWithCriteria({ types: ["COMPONENT"] });
> return JSON.stringify(comps.filter(c => c.parent?.name?.toLowerCase().includes("YOUR_COMPONENT_NAME"))
>   .map(c => ({ compSet: c.parent?.name, variant: c.name, key: c.key })).slice(0, 20));
> ```
