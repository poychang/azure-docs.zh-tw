# 概觀
## [什麼是 Azure Active Directory？](active-directory-whatis.md)
## [關於 Azure 身分識別管理](identity-fundamentals.md)
## [了解 Azure 身分識別解決方案](understand-azure-identity-solutions.md)
## [選擇混合式身分識別解決方案](choose-hybrid-identity-solution.md)
## [關聯 Azure 訂用帳戶](active-directory-how-subscriptions-associated-directory.md)
## [常駐和資料考量](active-directory-data-storage-eu.md)
## [常見問題集](active-directory-faq.md)
## [新功能](whats-new.md)


# 開始使用
## [開始使用 Azure AD](get-started-azure-ad.md)
## [註冊 Azure AD Premium](active-directory-get-started-premium.md)
## [新增自訂網域名稱](add-custom-domain.md)
## [設定公司商標](customize-branding.md)
## [在 Azure AD 中新增使用者](add-users-azure-active-directory.md)
## [將授權指派給使用者](license-users-groups.md)
## [啟用自助式密碼重設](authentication/quickstart-sspr.md)
## [在 Azure AD 中新增貴組織的隱私權資訊](active-directory-properties-area.md)


# 作法
## 規劃和設計
### [了解 Azure AD 架構](active-directory-architecture.md)
### [Azure Active Directory 中的宣告對應](active-directory-claims-mapping.md)
### [部署混合式身分識別解決方案](active-directory-hybrid-identity-design-considerations-overview.md)
#### 判斷需求
##### [身分識別](active-directory-hybrid-identity-design-considerations-business-needs.md)
##### [目錄同步](active-directory-hybrid-identity-design-considerations-directory-sync-requirements.md)
##### [多因素驗證](active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements.md)
##### [身分識別生命週期策略](active-directory-hybrid-identity-design-considerations-lifecycle-adoption-strategy.md)
#### [資料安全性的規劃](active-directory-hybrid-identity-design-considerations-data-protection-strategy.md)
##### [資料保護](active-directory-hybrid-identity-design-considerations-dataprotection-requirements.md)
##### [內容管理](active-directory-hybrid-identity-design-considerations-contentmgt-requirements.md)
##### [存取控制](active-directory-hybrid-identity-design-considerations-accesscontrol-requirements.md)
##### [事件回應](active-directory-hybrid-identity-design-considerations-incident-response-requirements.md)
#### 規劃身分識別生命週期
##### [工作](active-directory-hybrid-identity-design-considerations-hybrid-id-management-tasks.md)
##### [採用策略](active-directory-hybrid-identity-design-considerations-identity-adoption-strategy.md)
#### [後續步驟](active-directory-hybrid-identity-design-considerations-nextsteps.md)
#### [工具比較](active-directory-hybrid-identity-design-considerations-tools-comparison.md)

## 管理使用者
### [在 Azure AD 中新增使用者](add-users-azure-active-directory.md)
### [管理使用者設定檔](active-directory-users-profile-azure-portal.md)
### [共用帳戶](active-directory-sharing-accounts.md)
### [將使用者指派為管理員角色](active-directory-users-assign-role-azure-portal.md)
### [從另一個目錄 (B2B) 中新增來賓使用者](b2b/what-is-b2b.md)
#### [管理員新增 B2B 使用者](b2b/add-users-administrator.md)
#### [資訊背景工作新增 B2B 使用者](b2b/add-users-information-worker.md)
#### [API 與自訂](b2b/customize-invitation-api.md)
#### [程式碼和 Azure PowerShell 範例](b2b/code-samples.md)
#### [自助入口網站註冊範例](b2b/self-service-portal.md)
#### [邀請電子郵件](b2b/invitation-email-elements.md)
#### [兌換邀請](b2b/redemption-experience.md)
#### [在沒有邀請的情況下新增 B2B 使用者](b2b/add-user-without-invite.md)
#### [允許或封鎖邀請](b2b/allow-deny-list.md)
#### [B2B 的條件式存取](b2b/conditional-access.md)
#### [B2B 共用原則](b2b/delegate-invitations.md)
#### [將 B2B 使用者新增至角色](b2b/add-guest-to-role.md)
#### [動態群組和 B2B 使用者](b2b/use-dynamic-groups.md)
#### [離開組織](b2b/leave-the-organization.md)
#### [稽核與報告](b2b/auditing-and-reporting.md)
#### [適用於混合式組織的 B2B](b2b/hybrid-organizations.md)
##### [授與 B2B 使用者本機應用程式的存取權限](b2b/hybrid-cloud-to-on-premises.md)
##### [授與本機使用者雲端應用程式的存取權限](b2b/hybrid-on-premises-to-cloud.md)
#### [B2B 和 Office 365 外部共用](b2b/o365-external-user.md)
#### [B2B 授權](b2b/licensing-guidance.md)
#### [目前限制](b2b/current-limitations.md)
#### [常見問題集](b2b/faq.md)
#### [疑難排解 B2B](b2b/troubleshoot.md)
#### [了解 B2B 使用者](b2b/user-properties.md)
#### [B2B 使用者權杖](b2b/user-token.md)
#### [適用於 Azure AD 整合應用程式的 B2B](b2b/configure-saas-apps.md)
#### [B2B 使用者宣告對應](b2b/claims-mapping.md)
#### [比較 B2B 共同作業與 B2C](b2b/compare-with-b2c.md)
#### [取得 B2B 支援](b2b/get-support.md)

## [管理群組和成員](active-directory-manage-groups.md)
### 管理群組
#### [Azure 入口網站](active-directory-groups-create-azure-portal.md)
#### [Azure PowerShell](active-directory-accessmanagement-groups-settings-v2-cmdlets.md)
### [管理群組成員](active-directory-groups-members-azure-portal.md)
### [管理群組擁有者](active-directory-accessmanagement-managing-group-owners.md)
### [管理群組成員資格](active-directory-groups-membership-azure-portal.md)
### [使用群組指派授權](active-directory-licensing-whatis-azure-portal.md)
#### [將授權指派給群組](active-directory-licensing-group-assignment-azure-portal.md)
#### [識別並解決群組的授權問題](active-directory-licensing-group-problem-resolution-azure-portal.md)
#### [將個別授權使用者移轉至群組型的授權](active-directory-licensing-group-migration-azure-portal.md)
#### [群組型授權的其他案例](active-directory-licensing-group-advanced.md)
#### [群組型授權的 Azure PowerShell 範例](active-directory-licensing-ps-examples.md)
#### [Azure AD 中的產品與服務方案的參考](active-directory-licensing-product-and-service-plan-reference.md)
### [設定 Office 365 群組到期時間](active-directory-groups-lifecycle-azure-portal.md)
### [檢視全部群組](active-directory-groups-view-azure-portal.md)
### [新增 SaaS 應用程式的群組存取權](active-directory-accessmanagement-group-saasapps.md)
### [還原已刪除的 Office 365 群組](active-directory-groups-restore-azure-portal.md)
### 管理群組設定
#### [Azure 入口網站](active-directory-groups-settings-azure-portal.md)
#### [Cmdlet](active-directory-accessmanagement-groups-settings-cmdlets.md)
### 建立進階規則
#### [Azure 入口網站](active-directory-groups-dynamic-membership-azure-portal.md)
### [設定自助式群組](active-directory-accessmanagement-self-service-group-management.md)
### [疑難排解](active-directory-accessmanagement-troubleshooting.md)

## [管理報告](active-directory-reporting-azure-portal.md)
### [登入活動](active-directory-reporting-activity-sign-ins.md)
### [稽核活動](active-directory-reporting-activity-audit-logs.md)
### [有風險的使用者](active-directory-reporting-security-user-at-risk.md)
### [有風險的登入](active-directory-reporting-security-risky-sign-ins.md)
### [風險事件](active-directory-reporting-risk-events.md)
### [常見問題集](active-directory-reporting-faq.md)
### 工作
#### [設定具名位置](active-directory-named-locations.md)
#### [尋找活動報告](active-directory-reporting-migration.md)
#### [使用 Azure Active Directory Power BI 內容套件](active-directory-reporting-power-bi-content-pack-how-to.md)
### 參考
#### [保留](active-directory-reporting-retention.md)
#### [延遲](active-directory-reporting-latencies-azure-portal.md)
#### [通知](active-directory-reporting-notifications.md)
#### [稽核活動參考](active-directory-reporting-activity-audit-reference.md)
#### [登入活動的錯誤代碼](active-directory-reporting-activity-sign-ins-errors.md)
#### [Multi-Factor Authentication](active-directory-reporting-activity-sign-ins-mfa.md)
### 疑難排解
#### [缺少稽核資料](active-directory-reporting-troubleshoot-missing-audit-data.md)
#### [下載中缺少的資料](active-directory-reporting-troubleshoot-missing-data-download.md)
#### [Azure Active Directory 活動記錄內容套件錯誤](active-directory-reporting-troubleshoot-content-pack.md)
### [程式設計存取](active-directory-reporting-api-getting-started-azure-portal.md)
#### [稽核參考](active-directory-reporting-api-audit-reference.md)
#### [登入參考](active-directory-reporting-api-sign-in-activity-reference.md)
#### [先決條件](active-directory-reporting-api-prerequisites-azure-portal.md)
#### [稽核範例](active-directory-reporting-api-audit-samples.md)
#### [登入範例](active-directory-reporting-api-sign-in-activity-samples.md)
#### [使用憑證](active-directory-reporting-api-with-certificates.md)

## 管理密碼
### [密碼概觀](authentication/active-directory-passwords-overview.md)
### 使用者文件
#### [重設或變更您的密碼](active-directory-passwords-update-your-own-password.md)
#### [密碼最佳做法](active-directory-secure-passwords.md)
#### [註冊自助式密碼重設](active-directory-passwords-reset-register.md)
### [SSPR 運作方式](authentication/concept-sspr-howitworks.md)
### [SSPR 部署指南](authentication/howto-sspr-deployment.md)
### [SSPR 和 Windows 10](authentication/tutorial-sspr-windows.md)
### [SSPR 原則](authentication/concept-sspr-policy.md)
### [SSPR 自訂](authentication/concept-sspr-customization.md)
### [SSPR 資料需求](authentication/howto-sspr-authenticationdata.md)
### [SQL 報告](authentication/howto-sspr-reporting.md)
### IT 系統管理員︰重設密碼
#### [Azure 入口網站](active-directory-users-reset-password-azure-portal.md)
### [授權 SSPR](authentication/concept-sspr-licensing.md)
### [密碼回寫](authentication/howto-sspr-writeback.md)
### [疑難排解](authentication/active-directory-passwords-troubleshoot.md)
### [常見問題集](authentication/active-directory-passwords-faq.md)


## 管理裝置
### [簡介](device-management-introduction.md)
### [使用 Azure 入口網站](device-management-azure-portal.md)
### [規劃 Azure AD Join](active-directory-azureadjoin-deployment-aadjoindirect.md)
### [常見問題集](device-management-faq.md)
### 工作
#### [設定 10 部已註冊 Azure AD 的 Windows 10 裝置](device-management-azuread-registered-devices-windows10-setup.md)
#### [設定 Azure AD 已加入裝置](device-management-azuread-joined-devices-setup.md)
#### [設定混合式 Azure AD 已加入裝置](device-management-hybrid-azuread-joined-devices-setup.md)
#### [部署內部部署](active-directory-device-registration-on-premises-setup.md)
#### [在第一次執行 Windows 10 時加入 Azure AD 的體驗](device-management-azuread-joined-devices-frx.md)
### 疑難排解
#### [混合式 Azure AD 已加入 Windows 10 和 Windows Server 2016 裝置](device-management-troubleshoot-hybrid-join-windows-current.md)
#### [混合式 Azure AD 已加入舊版 Windows 裝置](device-management-troubleshoot-hybrid-join-windows-legacy.md)

## 管理應用程式
### [概觀](manage-apps/what-is-application-management.md)
### [開始使用](manage-apps/plan-an-application-integration.md)
### [SaaS 應用程式整合教學課程](active-directory-saas-tutorial-list.md)
### [Cloud App Discovery](manage-apps/cloud-app-discovery.md)
#### [建立快照集報告](manage-apps/cloud-app-discovery-create-snapshot-reports.md)
#### [設定連續報告](https://docs.microsoft.com/cloud-app-security/discovery-docker)
#### [使用自訂記錄剖析器](https://docs.microsoft.com/cloud-app-security/custom-log-parser)


### [透過 App Proxy 遠端存取應用程式](manage-apps/application-proxy.md)
#### 開始使用
##### [啟用應用程式 Proxy](manage-apps/application-proxy-enable.md)
##### [發佈應用程式](manage-apps/application-proxy-publish-azure-portal.md)
##### [自訂網域](manage-apps/application-proxy-configure-custom-domain.md)
#### [單一登入](manage-apps/application-proxy-single-sign-on.md)
##### [搭配 KCD 的 SSO](manage-apps/application-proxy-configure-single-sign-on-with-kcd.md)
##### [搭配標頭的 SSO](manage-apps/application-proxy-configure-single-sign-on-with-ping-access.md)
##### [搭配密碼保存庫的 SSO](manage-apps/application-proxy-configure-single-sign-on-password-vaulting.md)
#### 概念
##### [連接器](manage-apps/application-proxy-connectors.md)
##### [Security](manage-apps/application-proxy-security.md)
##### [網路](manage-apps/application-proxy-network-topology.md)


##### [從 TMG 或 UAG 升級](manage-apps/application-proxy-migration.md)

#### 進階組態
##### [在不同網路上發佈](manage-apps/application-proxy-connector-groups.md)
##### [Proxy 伺服器](manage-apps/application-proxy-configure-connectors-with-proxy-servers.md)
##### [宣告感知應用程式](manage-apps/application-proxy-configure-for-claims-aware-applications.md)
##### [原生用戶端應用程式](manage-apps/application-proxy-configure-native-client-application.md)
##### [無訊息安裝](manage-apps/application-proxy-register-connector-powershell.md)
##### [自訂首頁](manage-apps/application-proxy-configure-custom-home-page.md)
##### [翻譯內嵌連結](manage-apps/application-proxy-configure-hard-coded-link-translation.md)
##### [萬用字元](active-directory-application-proxy-wildcard.md)
##### [移除個人資料](manage-apps/application-proxy-remove-personal-data.md)


#### 發佈逐步解說
##### [遠端桌面](manage-apps/application-proxy-integrate-with-remote-desktop-services.md)
##### [SharePoint](manage-apps/application-proxy-integrate-with-sharepoint-server.md)
##### [Microsoft Teams](application-proxy-teams.md)
##### [Tableau](active-directory-application-proxy-tableau.md)
##### [Qlik](active-directory-application-proxy-qlik.md)


#### [疑難排解](active-directory-application-proxy-troubleshoot.md)

### 管理企業應用程式
#### [指派使用者](active-directory-coreapps-assign-user-azure-portal.md)
#### [自訂商標](active-directory-coreapps-change-app-logo-user-azure-portal.md)
#### [停用使用者登入](active-directory-coreapps-disable-app-azure-portal.md)
#### [移除使用者](active-directory-coreapps-remove-assignment-azure-portal.md)
#### [檢視我的所有應用程式](active-directory-coreapps-view-azure-portal.md)
#### [管理使用者帳戶佈建](active-directory-enterprise-apps-manage-provisioning.md)
#### [管理企業應用程式的單一登入](active-directory-enterprise-apps-manage-sso.md)
#### [適用於 SAML 應用程式的進階憑證](active-directory-enterprise-apps-advance-certificate-options.md)
#### [隱藏使用者的第三方應用程式經驗](active-directory-coreapps-hide-third-party-app.md)
### [使用 HRD 原則設定登入時自動加速](active-directory-auto-acceleration-using-hrd.md)

### [管理應用程式的存取權](active-directory-managing-access-to-apps.md)
#### [SSO 存取](manage-apps/what-is-single-sign-on.md)
#### [SSO 憑證](active-directory-sso-certs.md)
#### [租用戶限制](active-directory-tenant-restrictions.md)
#### [使用 SCIM 佈建使用者](active-directory-scim-provisioning.md)

### [疑難排解](active-directory-application-troubleshoot-content-map.md)
#### [應用程式開發](active-directory-application-dev-troubleshoot-content-map.md)
##### [設定和註冊](active-directory-application-dev-config-content-map.md)
##### [開發](active-directory-application-dev-development-content-map.md)
#### [應用程式管理](active-directory-application-management-troubleshoot-content-map.md)
##### [組態](active-directory-application-config-content-map.md)
##### [登入](active-directory-application-sign-in-content-map.md)
##### [佈建](active-directory-application-provisioning-content-map.md)
##### [管理存取](active-directory-application-access-content-map.md)
##### [存取面板](active-directory-application-access-panel-content-map.md)
##### [應用程式 Proxy](active-directory-application-proxy-content-map.md)
##### [條件式存取](active-directory-application-conditional-access-content-map.md)
### [開發應用程式](active-directory-applications-guiding-developers-for-lob-applications.md)
### [文件庫](active-directory-apps-index.md)

## 管理您的目錄
### [Azure AD Connect](./connect/active-directory-aadconnect.md)
### 自訂網域名稱
#### [快速入門](add-custom-domain.md)
#### [新增自訂網域名稱](active-directory-domains-manage-azure-portal.md)
### [管理目錄](active-directory-administer.md)
### [多個目錄](active-directory-licensing-directory-independence.md)
### [自助式註冊](active-directory-self-service-signup.md)
### [接管非受控目錄](domains-admin-takeover.md)
### [企業狀態漫遊](active-directory-windows-enterprise-state-roaming-overview.md)
#### [啟用](active-directory-windows-enterprise-state-roaming-enable.md)
#### [群組原則設定](active-directory-windows-enterprise-state-roaming-group-policy-settings.md)
#### [Windows 10 設定](active-directory-windows-enterprise-state-roaming-windows-settings-reference.md)
#### [常見問題集](active-directory-windows-enterprise-state-roaming-faqs.md)
#### [疑難排解](active-directory-windows-enterprise-state-roaming-troubleshooting.md)


### [使用 Azure AD Connect 整合內部部署身分識別](./connect/active-directory-aadconnect.md)

## [管理 Azure 的存取權](../role-based-access-control/toc.yml)

## 委派資源存取
### [管理員角色](active-directory-assign-admin-roles-azure-portal.md)
#### [指派管理員角色](active-directory-users-assign-role-azure-portal.md)
#### [預設使用者權限](users-default-permissions.md)
### [管理單位](active-directory-administrative-units-management.md)
### [設定權杖存留期](active-directory-configurable-token-lifetimes.md)
### [管理緊急存取管理帳戶](active-directory-admin-manage-emergency-access-accounts.md)
### [保護特殊權限角色](admin-roles-best-practices.md)

## 存取權檢閱
### [存取權檢閱概觀](active-directory-azure-ad-controls-access-reviews-overview.md)
### [完成存取權檢閱](active-directory-azure-ad-controls-complete-access-review.md)
### [建立存取權檢閱](active-directory-azure-ad-controls-create-access-review.md)
### [開始執行存取權檢閱](active-directory-azure-ad-controls-perform-access-review.md)
### [如何檢閱您的存取權](active-directory-azure-ad-controls-how-to-review-your-access.md)
### [透過存取權檢閱進行來賓存取](active-directory-azure-ad-controls-manage-guest-access-with-access-reviews.md)
### [透過檢閱管理使用者存取](active-directory-azure-ad-controls-manage-user-access-with-access-reviews.md)
### [管理程式和控制項](active-directory-azure-ad-controls-manage-programs-controls.md)
### [取出存取權檢閱結果](active-directory-azure-ad-controls-retrieve-access-review.md)

## 保護您的身分識別
### [條件式存取](active-directory-conditional-access-azure-portal.md)
#### [條件](active-directory-conditional-access-conditions.md)
#### [位置條件](active-directory-conditional-access-locations.md)
#### [控制項](active-directory-conditional-access-controls.md)
#### [開始使用](active-directory-conditional-access-azure-portal-get-started.md)
#### [最佳做法](active-directory-conditional-access-best-practices.md)
#### [了解 Office 365 服務的裝置原則](active-directory-conditional-access-device-policies.md)
#### [移轉傳統原則](active-directory-conditional-access-migration.md)
#### [假設工具](active-directory-conditional-access-whatif.md)
#### 快速入門
##### [設定每個雲端應用程式 MFA](active-directory-conditional-access-app-based-mfa.md)
#### 工作
##### [移轉傳統 MFA 原則](active-directory-conditional-access-migration-mfa.md)
##### [設定裝置型條件式存取](active-directory-conditional-access-policy-connected-applications.md)
##### [設定應用程式型條件式存取](active-directory-conditional-access-mam.md)
##### [為使用者和應用程式提供使用規定](active-directory-tou.md)
##### [設定 VPN 連線能力](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy)
##### [設定 SharePoint 和 Exchange Online](active-directory-conditional-access-no-modern-authentication.md)
##### [補救](active-directory-conditional-access-device-remediation.md)
#### [技術參考](active-directory-conditional-access-technical-reference.md)
#### [常見問題集](active-directory-conditional-faqs.md)

### Windows Hello
#### [無需密碼驗證](active-directory-azureadjoin-passport.md)
#### [啟用 Windows Hello 企業版](active-directory-azureadjoin-passport-deployment.md)
### 憑證式驗證
#### [Android](active-directory-certificate-based-authentication-android.md)
#### [iOS](active-directory-certificate-based-authentication-ios.md)
#### [開始使用](active-directory-certificate-based-authentication-get-started.md)

### [Azure AD Identity Protection](active-directory-identityprotection.md)
#### [啟用](active-directory-identityprotection-enable.md)
#### [偵測弱點](active-directory-identityprotection-vulnerabilities.md)
#### [風險事件](active-directory-identity-protection-risk-events.md)
#### [通知](active-directory-identityprotection-notifications.md)
#### [登入體驗](active-directory-identityprotection-flows.md)
#### [模擬風險事件](active-directory-identityprotection-playbook.md)
#### [解除封鎖使用者](active-directory-identityprotection-unblock-howto.md)
#### [常見問題集](active-directory-identity-protection-faqs.md)
#### [詞彙](active-directory-identityprotection-glossary.md)
#### [Microsoft Graph](active-directory-identityprotection-graph-getting-started.md)
### [Privileged Identity Management](active-directory-privileged-identity-management-configure.md)

## [將其他服務與 Azure AD 整合]()
### [啟用 LinkedIn 整合](linkedin-integration.md)

## [在 Azure 中部署 AD FS](active-directory-aadconnect-azure-adfs.md)
### [高可用性](active-directory-adfs-in-azure-with-azure-traffic-manager.md)
### [變更簽章雜湊演算法](active-directory-federation-sha256-guidance.md)

## [疑難排解](active-directory-troubleshooting-support-howto.md)

## 部署 Azure AD 概念證明 (PoC)
### [PoC 腳本：簡介](active-directory-playbook-intro.md)
### [PoC 腳本：因素](active-directory-playbook-ingredients.md)
### [PoC 腳本：實作](active-directory-playbook-implementation.md)
### [PoC 腳本：建置區塊](active-directory-playbook-building-blocks.md)


# 參考
## [程式碼範例](https://azure.microsoft.com/resources/samples/?service=active-directory)
## [Azure PowerShell Cmdlet](/powershell/azure/overview)
## [Java API 參考](/java/api)
## [.NET API](/active-directory/adal/microsoft.identitymodel.clients.activedirectory)
## [服務限制](active-directory-service-limits-restrictions.md)

# 相關參考
## [Multi-Factor Authentication](/azure/multi-factor-authentication/)
## [Azure AD Connect](./connect/active-directory-aadconnect.md)
## [Azure AD Connect Health](./connect-health/active-directory-aadconnect-health.md)
## [開發人員適用的 Azure AD](./develop/active-directory-how-to-integrate.md)
## [Azure AD Privileged Identity Management](./privileged-identity-management/active-directory-securing-privileged-access.md)

# 資源
## [Azure 意見反應論壇](https://feedback.azure.com/forums/169401-azure-active-directory)
## [Azure 藍圖](https://azure.microsoft.com/roadmap/?category=security-identity)
## [MSDN 論壇](https://social.msdn.microsoft.com/Forums/azure/en-US/home?forum=WindowsAzureAD)
## [定價](https://azure.microsoft.com/pricing/details/active-directory/)
## [定價計算機](https://azure.microsoft.com/pricing/calculator/)
## [服務更新](https://azure.microsoft.com/updates/?product=active-directory)
## [Stack Overflow](http://stackoverflow.com/questions/tagged/azure-active-directory)
## [影片](https://azure.microsoft.com/documentation/videos/index/?services=active-directory)
