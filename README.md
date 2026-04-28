# Analysis-Driven System Architect Portfolio

> **"Eliminating guesswork, building on physical evidence."**

OSの低レイヤーからネットワーク、アプリケーションロジックまで、解析によって得た知見をアーキテクチャに還元し、システムの堅牢化と運用自動化を完遂するエキスパート・エンジニアです。

ベンダーが解決不能としたOSバグや製品競合を、WinDbgによるメモリダンプ解析やバイナリレベルでの調査を通じて特定し、システムを『本来あるべき設計・パフォーマンス』へと回帰させることを信条としています。

---

## Technical Core & Edge

### 1. Deep Analysis & Troubleshooting
- **Memory Analysis**: WinDbgを用いたプロダクション環境のメモリダンプ解析、Non-Paged Poolリークの特定。
- **Binary Level Investigation**: Windows/Linuxカーネルの内部不整合の特定、ベンダー製品の隠れた挙動の解明。
- **Network Analysis**: Wiresharkによるパケット解析およびプロトコルスタックの不具合診断。

### 2. Engineering & Implementation
- **Languages**: **Go, Python, Kotlin, PHP (Laravel)** をプロジェクトに応じて使い分けるマルチスタック志向。
- **Low-Level Dev**: Android BLE P2Pプロトコル設計など、OS制約を突破する高効率なバックグラウンド処理の実装。
- **AI-Co-Development**: Claude Code等のAIエージェントを「高度な補助輪」とし、解析深度の向上とプロトタイピングを加速。

---

## Featured Repositories

### [low_layer / Windows Memory Analysis](https://github.com/hanakata/low_layer/tree/main/Windows/memory)
「物理的な証拠」を積み上げるための解析スクリプト群。
- `NonPagedPool_leak`: カーネルメモリリークの動的追跡。
- `VirtualAlloc_Usage`: プロセスごとのメモリ確保状況の可視化。
- **Purpose**: ブラックボックス化したOS挙動を可視化し、エビデンスベースの意思決定を支援する。

### [BLE P2P Protocol Design (CLAUDE.md)](./CLAUDE.md)
Android OSの厳しい制限下で動作する、低消費電力P2Pプロトコルの設計指針。
- **Constraint Handling**: Android 12-15のバックグラウンド制限の回避。
- **Binary Efficiency**: 20バイトの制限内でCRC16を含む高密度パケット構造を設計。

---

## Key Achievements

* **Financial Mission-Critical Support**: 
    「再起動不可」の条件下で、カーネルメモリの断片化（Fragmentation）をslabinfoから特定。物理エビデンスによる合意形成を主導し、異例の緊急メンテナンスを完遂。
* **Security Product Conflict Resolution**: 
    EDRとIllumioのDLL Injection競合をWinDbgで解析。ベンダー未把握の不具合を論理的に証明し、ビジネス損失を回避。
* **Infrastructure Optimization**: 
    Windows ServerのOS内部データ不整合を特定。全社規模の開発標準設定をエビデンスベースで抜本修正。

---

## Engineering Philosophy

1. **Zero Assumption**: 「おそらく」を排し、バイナリやログという物理的な証拠からのみ真実を導き出す。
2. **Design for Failure**: 冪等性の担保を徹底し、中断箇所からの再開が常に安全なシステムを構築する。
3. **The Last Bastion**: ベンダーが匙を投げた問題の「最後の砦（Tier 3/4）」として、解決策を提示する責任。

---

## Contact & Links

- **Role**: Expert Engineer / System Architect
- **Specialties**: Kernel Analysis, Cybersecurity, Full-layer System Design
- **Business Value**: 技術的判断をビジネスの収益性・リスクに直結させて判断できる、経営的視点を備えたエンジニアリング。

---
&copy; 2026 Analysis-Driven System Architect
