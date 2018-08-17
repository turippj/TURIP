# TURIPのポートマップ

本資料は、TURIPの各ポートの機能を表にまとめたものです。
空白部分は未定義です。今後の機能拡張で利用される予定です。

## 0x00(0) - 0x3f(63): アプリケーション領域(PORTS_APPLICATION)

アプリケーション領域は、開発者が自由に定義して利用できる領域です。

ポート             | 型 | 名称             | R/W | 機能                               |
-------------------|----|------------------|-----|------------------------------------|
0x00(0) - 0x3f(63) | -  | PORTS_APPLICATION | -   | 開発者が自由に使用できる領域です。 |

## 0x40(64) - 0x7f(127): システム領域(PORTS_SYSTEM)

システム領域にはTURIPの動作に必要な設定情報が含まれています。

ポート    | 型     | 名称                         | R/W           | 機能                                                                                                             |
----------|--------|------------------------------|---------------|------------------------------------------------------------------------------------------------------------------|
0x40(64)  | uint32 | PORT_MODEL                   | RO or RW_LOCK | TURIPデバイスの型番です。                                                                                        |
0x41(65)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x43(66)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x43(67)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x44(68)  | uint32 | PORT_SERIAL                  | RO or RW_LOCK | TURIPデバイスのシリアル番号です。未設定の場合、0とします。                                                       |
0x45(69)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x46(70)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x47(71)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x48(72)  | uint32 | PORT_SPI_MAX_SPEED           | RO            | SPIの最大速度[bps]です。SPIインターフェイスが無い場合は0とします。                                               |
0x49(73)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x4A(74)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x4B(75)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x4C(76)  | uint8  | PORT_SPI_MIN_DELAY           | RO            | SPIにおける1バイト送受信時に最低限遅延させなければならない時間[us]です。                                         |
0x4D(77)  | uint8  | PORT_SPI_HUB_SOCKETS         | RO            | SPIハブ機能のソケット数です。非対応の場合は0とします。                                                           |
0x4E(78)  | uint8  | PORT_SPI_HUB_SELECT          | RW            | SPIハブ機能によってデバイスを選択します。無選択の場合は0とします。                                               |
0x4F(79)  |        |                              |               |                                                                                                                  |
0x50(80)  | uint32 | PORT_I2C_MAX_SPEED           | RO            | I2Cの最大速度[bps]です。I2Cインターフェイスが無い場合は0とします。                                               |
0x51(81)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x52(82)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x53(83)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x54(84)  | uint8  | PORT_I2C_ADDR                | RW_LOCK       | I2Cアドレスです(0-127)。                                                                                         |
0x55(85)  |        |                              |               |                                                                                                                  |
0x56(86)  |        |                              |               |                                                                                                                  |
0x57(87)  |        |                              |               |                                                                                                                  |
0x58(88)  | uint32 | PORT_UART_BAUD_RATE          | RW_LOCK       | UARTのボーレート[bps]です。UARTインターフェイスが無い場合は0とします。                                           |
0x59(89)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x5A(90)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x5B(91)  | -      | (RESERVED)                   | -             |                                                                                                                  |
0x5C(92)  | uint8  | PORT_UART_MULTI_ENABLE       | RW_LOCK       | UARTの複数接続機能の有効・無効を設定します。有効は1、無効は0です。                                               |
0x5D(93)  | uint8  | PORT_UART_MULTI_CA           | RW_LOCK       | UARTの伝送路上の衝突回避(CA)を行います。格納した時間[us]内のランダムな時間でデータを送出します。                 |
0x5E(94)  |        |                              |               |                                                                                                                  |
0x5F(95)  |        |                              |               |                                                                                                                  |
0x60(96)  | uint8  | PORT_IPV4_ADDR_PORT          | RO            | IPv4アドレスを格納しているアプリケーション領域(APPLICATION_AREA)のポート番号を示します。無い場合は0xffです。     |
0x61(97)  | uint8  | PORT_IPV6_ADDR_PORT          | RO            | IPv6アドレスを格納しているアプリケーション領域(APPLICATION_AREA)のポート番号を示します。無い場合は0xffです。     |
0x62(98)  | uint8  | PORT_MAC_ADDR_PORT           | RO            | MACアドレスを格納しているアプリケーション領域(APPLICATION_AREA)のポート番号を示します。無い場合は0xffです。      |
0x63(99)  | uint8  | PORT_DHCP_ENABLE             | RW_LOCK       | DHCPによるIPアドレス設定の有効・無効を選択します。(0:無効、1:有効)                                               |
0x64(100) | uint8  | PORT_WIFI_MODE               | RW_LOCK       | Wifiのモード選択をします。(0:無効、1:インフラストラクチャーモード、2:アドホックモード)                           |
0x65(101) | uint8  | PORT_WIFI_SSID_PORT          | RO            | WifiのSSIDを格納しているアプリケーション領域(APPLICATION_AREA)のポート番号を示します。無い場合は0xffです。       |
0x66(102) | uint8  | PORT_WIFI_PASS_PORT          | RO            | Wifiのパスワードを格納しているアプリケーション領域(APPLICATION_AREA)のポート番号を示します。無い場合は0xffです。 |
0x67(103) |        |                              |               |                                                                                                                  |
0x68(104) |        |                              |               |                                                                                                                  |
0x69(105) |        |                              |               |                                                                                                                  |
0x6A(106) |        |                              |               |                                                                                                                  |
0x6B(107) |        |                              |               |                                                                                                                  |
0x6C(108) |        |                              |               |                                                                                                                  |
0x6D(109) |        |                              |               |                                                                                                                  |
0x6E(110) |        |                              |               |                                                                                                                  |
0x6F(111) |        |                              |               |                                                                                                                  |
0x70(112) |        |                              |               |                                                                                                                  |
0x71(113) |        |                              |               |                                                                                                                  |
0x72(114) |        |                              |               |                                                                                                                  |
0x73(115) |        |                              |               |                                                                                                                  |
0x74(116) |        |                              |               |                                                                                                                  |
0x75(117) |        |                              |               |                                                                                                                  |
0x76(118) |        |                              |               |                                                                                                                  |
0x77(119) |        |                              |               |                                                                                                                  |
0x78(120) |        |                              |               |                                                                                                                  |
0x79(121) |        |                              |               |                                                                                                                  |
0x7A(122) |        |                              |               |                                                                                                                  |
0x7B(123) | uint8  | PORT_DEVICE_VERSION          | RO            | デバイスのバージョンです。                                                                                       |
0x7C(124) | uint8  | PORT_TURIP_VERSION           | RO            | TURIPのバージョンです。                                                                                          |
0x7D(125) | uint8  | PORT_CONFIG_LOCK             | RW            | 0x55格納されるとロックされた設定データ(RW_LOCK)を変更できるようになります。                                      |
0x7E(126) | uint8  | PORT_SOFTWARE_RESET          | RW            | 0x00が格納されるとモジュールはリセット動作を行います。それ以外の値は何もしません。                               |
0x7F(127) | uint8  | NULL(0xff) / DATA_WAIT(0x7f) | -             | 無信号状態の時に用いられます(0xff)。また、モジュールからのプッシュを待機するときは0x7fを送ります。               |
