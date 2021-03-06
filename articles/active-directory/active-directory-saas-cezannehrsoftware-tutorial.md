---
title: 教學課程：Azure Active Directory 與 Cezanne HR Software 整合 | Microsoft Docs
description: 了解如何設定 Azure Active Directory 與 Cezanne HR Software 之間的單一登入。
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.reviewer: joflore
ms.assetid: 62b42e15-c282-492d-823a-a7c1c539f2cc
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 11/28/2017
ms.author: jeedes
ms.openlocfilehash: b6ba41b31df8f950e37724903d3bca31358a598c
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2018
---
# <a name="tutorial-azure-active-directory-integration-with-cezanne-hr-software"></a>教學課程：Azure Active Directory 與 Cezanne HR Software 整合

在此教學課程中，您將了解如何整合 Cezanne HR Software 與 Azure Active Directory (Azure AD)。

Cezanne HR Software 與 Azure AD 整合提供下列優點：

- 您可以在 Azure AD 中控制可存取 Cezanne HR Software 的人員。
- 您可以讓使用者使用他們的 Azure AD 帳戶自動登入 Cezanne HR Software (單一登入)。
- 您可以在 Azure 入口網站中集中管理您的帳戶。

如果您想要了解有關 SaaS 應用程式與 Azure AD 之整合的更多詳細資料，請參閱[什麼是搭配 Azure Active Directory 的應用程式存取和單一登入](manage-apps/what-is-single-sign-on.md)。

## <a name="prerequisites"></a>先決條件

若要設定 Azure AD 與 Cezanne HR Software 整合，您需要以下項目：

- Azure AD 訂用帳戶
- 已啟用 Cezanne HR Software 單一登入的訂用帳戶

> [!NOTE]
> 若要測試本教學課程中的步驟，我們不建議使用生產環境。

若要測試本教學課程中的步驟，您應該遵循這些建議：

- 除非必要，否則請勿使用生產環境。
- 如果您沒有 Azure AD 試用環境，您可以[取得一個月試用](https://azure.microsoft.com/pricing/free-trial/)。

## <a name="scenario-description"></a>案例描述
在本教學課程中，您會在測試環境中測試 Azure AD 單一登入。 本教學課程中說明的案例由二項主要的基本工作組成：

1. 從資源庫加入 Cezanne HR Software
2. 設定並測試 Azure AD 單一登入

## <a name="adding-cezanne-hr-software-from-the-gallery"></a>從資源庫加入 Cezanne HR Software
若要設定 Cezanne HR Software 與 Azure AD 整合，您需要從資源庫將 Cezanne HR Software 新增到受控 SaaS 應用程式清單。

**若要從資源庫新增 Cezanne HR Software，請執行下列步驟：**

1. 在 **[Azure 入口網站](https://portal.azure.com)** 的左方瀏覽窗格中，按一下 [Azure Active Directory] 圖示。 

    ![Azure Active Directory 按鈕][1]

2. 瀏覽至 [企業應用程式]。 然後移至 [所有應用程式]。

    ![企業應用程式刀鋒視窗][2]
    
3. 若要新增新的應用程式，請按一下對話方塊頂端的 [新增應用程式] 按鈕。

    ![新增應用程式按鈕][3]

4. 在搜尋方塊中，輸入 **Cezanne HR Software**，從結果面板中選取 [Cezanne HR Software]，然後按一下 [新增] 按鈕以新增應用程式。

    ![結果清單中的 [Cezanne HR Software]](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>設定和測試 Azure AD 單一登入

在本節中，您會以名為 "Britta Simon" 的測試使用者為基礎，設定及測試與 Cezanne HR Software 搭配運作的 Azure AD 單一登入。

若要讓單一登入能夠運作，Azure AD 必須知道 Cezanne HR Software 與 Azure AD 中互相對應的使用者。 換句話說，Azure AD 使用者和 Cezanne HR Software 中的相關使用者之間必須建立連結關聯性。

在 Cezanne HR Software 中，將 Azure AD 中**使用者名稱**的值，指派為 **Username** 的值，以建立連結關聯性。

若要使用 Cezanne HR Software 設定並測試 Azure AD 單一登入，您需要完成下列建置組塊：

1. **[設定 Azure AD 單一登入](#configure-azure-ad-single-sign-on)** - 讓您的使用者能夠使用此功能。
2. **[建立 Azure AD 測試使用者](#create-an-azure-ad-test-user)** - 使用 Britta Simon 測試 Azure AD 單一登入。
3. **[建立 Cezanne HR Software 測試使用者](#create-a-cezannehrsoftware-test-user)** - 在 Cezanne HR Software 中建立一個與 Azure AD 中代表 Britta Simon 之項目連結的對應項目。
4. **[指派 Azure AD 測試使用者](#assign-the-azure-ad-test-user)** - 讓 Britta Simon 能夠使用 Azure AD 單一登入。
5. **[測試單一登入](#test-single-sign-on)**，驗證組態是否能運作。

### <a name="configure-azure-ad-single-sign-on"></a>設定 Azure AD 單一登入

在本節中，您會在 Azure 入口網站中啟用 Azure AD 單一登入，並在您的 Cezanne HR Software 應用程式中設定單一登入。

**若要使用 Cezanne HR Software 設定 Azure AD 單一登入，請執行下列步驟：**

1. 在 Azure 入口網站的 [Cezanne HR Software] 應用程式整合分頁上，按一下 [單一登入]。

    ![設定單一登入連結][4]

2. 在 [單一登入] 對話方塊上，於 [模式] 選取 [SAML 登入]，以啟用單一登入。
 
    ![單一登入對話方塊](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_samlbase.png)

3. 在 [Cezanne HR Software 網域及 URL] 區段上，執行下列步驟：

    ![Cezanne HR Software 網域與 URL 單一登入資訊](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_url.png)

    a. 在 [登入 URL] 文字方塊中，輸入 URL：`https://w3.cezanneondemand.com/CezanneOnDemand/-/<tenantidentifier>`

    b. 在 [識別碼] 文字方塊中，輸入 URL：`https://w3.cezanneondemand.com/CezanneOnDemand/`

    c. 在 [回覆 URL] 文字方塊中，輸入 URL：`https://w3.cezanneondemand.com:443/cezanneondemand/-/<tenantidentifier>/Saml/samlp`
    
    > [!NOTE]
    > 這些都不是真正的值。 請使用實際的「登入 URL」及「回覆 URL」來更新這些值。 若要取得這些值，請連絡 [Cezanne HR Software 用戶端支援小組](https://cezannehr.com/services/support/)。

4. 在 [SAML 簽署憑證] 區段上，按一下 [憑證 (Base64)]，然後將憑證檔案儲存在您的電腦上。

    ![憑證下載連結](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_certificate.png) 

5. 按一下 [儲存]  按鈕。

    ![設定單一登入儲存按鈕](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_general_400.png)

6. 在 [Cezanne HR Software 組態] 區段上，按一下 [設定 Cezanne HR Software] 以開啟 [設定登入] 視窗。

    ![Cezanne HR Software 設定](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_configure.png)

7. 向下捲動至 [快速參考] 區段。 從 [快速參考] 區段中複製 [SAML 單一登入服務 URL] 和 [SAML 實體識別碼]。

    ![Cezanne HR Software 設定](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_configure1.png)

8. 在不同的網頁瀏覽器視窗中，以系統管理員身分登入您的 Cezanne HR Software 租用戶。

9. 在左側的導覽窗格上，按一下 [系統設定] 。 移至 [安全性設定] 。 然後瀏覽至 [單一登入設定] 。

    ![在應用程式端設定單一登入](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_000.png)

10. 在 [允許使用者使用下列的單一登入 (SSO) 服務來登入] 面板中檢查 [SAML 2.0] 方塊，然後選取 [進階組態] 選項。

    ![在應用程式端設定單一登入](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_001.png)

11. 按一下 [新增]  按鈕。

    ![在應用程式端設定單一登入](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_002.png)

12. 在 [SAML 2.0 身分識別提供者]  區段中執行下列步驟。

    ![在應用程式端設定單一登入](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_003.png)
    
    a. 輸入識別提供者名稱做為**顯示名稱**。

    b. 在 [實體識別碼] 文字方塊中，貼上您從 Azure 入口網站複製的 [SAML 實體識別碼] 值。 

    c. 將 [SAML 繫結] 變更為 'POST'。

    d. 在 [Security Token Service 端點] 文字方塊中，貼上您從 Azure 入口網站複製的 [SAML 單一登入服務 URL] 值。

    e. 在 [使用者識別碼屬性名稱] 文字方塊中，輸入 `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`。
    
    f. 按一下 [上傳] 圖示來上傳從 Azure 入口網站下載的憑證。
    
    g. 按一下 [確定] 按鈕。 

13. 按一下 [儲存]  按鈕。

    ![在應用程式端設定單一登入](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_004.png)

> [!TIP]
> 現在，當您設定此應用程式時，在 [Azure 入口網站](https://portal.azure.com)內即可閱讀這些指示的簡要版本！  從 [Active Directory] > [企業應用程式] 區段新增此應用程式之後，只要按一下 [單一登入] 索引標籤，即可透過底部的 [組態] 區段存取內嵌的文件。 您可以從以下連結閱讀更多有關內嵌文件功能的資訊：[Azure AD 內嵌文件]( https://go.microsoft.com/fwlink/?linkid=845985)
> 

### <a name="create-an-azure-ad-test-user"></a>建立 Azure AD 測試使用者

本節的目標是要在 Azure 入口網站中建立一個名為 Britta Simon 的測試使用者。

   ![建立 Azure AD 測試使用者][100]

**若要在 Azure AD 中建立測試使用者，請執行下列步驟：**

1. 在 Azure 入口網站的左窗格中，按一下 [Azure Active Directory] 按鈕。

    ![Azure Active Directory 按鈕](./media/active-directory-saas-cezannehrsoftware-tutorial/create_aaduser_01.png)

2. 若要顯示使用者清單，請移至 [使用者和群組]，然後按一下 [所有使用者]。

    ![[使用者和群組] 與 [所有使用者] 連結](./media/active-directory-saas-cezannehrsoftware-tutorial/create_aaduser_02.png)

3. 若要開啟 [使用者] 對話方塊，按一下 [所有使用者] 對話方塊頂端的 [新增]。

    ![[新增] 按鈕](./media/active-directory-saas-cezannehrsoftware-tutorial/create_aaduser_03.png)

4. 在 [使用者] 對話方塊中，執行下列步驟：

    ![[使用者] 對話方塊](./media/active-directory-saas-cezannehrsoftware-tutorial/create_aaduser_04.png)

    a. 在 [名稱] 方塊中，輸入 **BrittaSimon**。

    b. 在 [使用者名稱] 方塊中，輸入使用者 Britta Simon 的電子郵件地址。

    c. 選取 [顯示密碼] 核取方塊，然後記下 [密碼] 方塊中顯示的值。

    d. 按一下頁面底部的 [新增] 。
 
### <a name="create-a-cezanne-hr-software-test-user"></a>建立 Cezanne HR Software 測試使用者

為了讓 Azure AD 使用者能夠登入 Cezanne HR Software，必須將他們佈建到 Cezanne HR Software 中。 Cezanne HR Software 需以手動的方式佈建。

**若要佈建使用者帳戶，請執行下列步驟：**

1.  以系統管理員身分登入您的 Cezanne HR Software 公司網站。

2.  在左側的導覽窗格上，按一下 [系統設定] 。 移至 [管理使用者] 。 然後瀏覽至 [新增使用者] 。

    ![新增使用者](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_005.png "新增使用者")

3.  在 [人員詳細資料]  區段中，執行下列步驟︰

    ![新增使用者](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_006.png "新增使用者")
    
    a. 將 [內部使用者] 設定為 OFF。
    
    b. 在 [名字] 文字方塊中，輸入使用者的名字，例如 **Britta**。  
 
    c. 在 [姓氏] 文字方塊中，輸入使用者的姓氏，例如 **Simon**。
    
    d. 在 [電子郵件] 文字方塊中，輸入像是 Brittasimon@contoso.com 的使用者電子郵件地址。

4.  在 [帳戶資訊]  區段中，執行下列步驟︰

    ![新增使用者](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_007.png "新增使用者")
    
    a. 在 [使用者名稱] 文字方塊中，輸入像是 Brittasimon@contoso.com 的使用者電子郵件。
    
    b. 在 [密碼] 文字方塊中，輸入使用者的密碼。
    
    c. 選取 [HR Professional] 做為 [安全性角色]。
    
    d. 按一下 [確定]。

5. 瀏覽至 [單一登入] 索引標籤並選取 [SAML 2.0 識別碼] 區域中的 [新增]。

    ![使用者](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_008.png "使用者")

6. 為 [識別提供者] 選擇識別提供者，並在 [使用者識別碼] 文字方塊中輸入 Britta Simon 帳戶的電子郵件地址。

    ![使用者](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_009.png "使用者")
    
7. 按一下 [儲存]  按鈕。

    ![使用者](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_010.png "使用者")

### <a name="assign-the-azure-ad-test-user"></a>指派 Azure AD 測試使用者

在本節中，您會把 Cezanne HR Software 的存取權授與 Britta Simon，讓她能夠使用 Azure 單一登入。

![指派使用者角色][200] 

**若要指派 Britta Simon 到 Cezanne HR Software，請執行以下步驟：**

1. 在 Azure 入口網站中，開啟應用程式檢視，接著瀏覽至目錄檢視並移至 [企業應用程式]，然後按一下 [所有應用程式]。

    ![指派使用者][201] 

2. 在應用程式清單中，選取 [Cezanne HR Software] 。

    ![應用程式清單中的 [Cezanne HR Software] 連結](./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_cezannehrsoftware_app.png)  

3. 在左側功能表中，按一下 [使用者和群組]。

    ![[使用者和群組] 連結][202]

4. 按一下 [新增] 按鈕。 然後選取 [新增指派] 對話方塊上的 [使用者和群組]。

    ![[新增指派] 窗格][203]

5. 在 [使用者和群組] 對話方塊上，選取 [使用者] 清單中的 [Britta Simon]。

6. 按一下 [使用者和群組] 對話方塊上的 [選取] 按鈕。

7. 按一下 [新增指派] 對話方塊上的 [指派] 按鈕。
    
### <a name="test-single-sign-on"></a>測試單一登入

在本節中，您會使用存取面板來測試您的 Azure AD 單一登入設定。

當您在 [存取面板] 中按一下 [Cezanne HR Software] 圖格時，您應該會自動登入您的 Cezanne HR Software 應用程式。
如需「存取面板」的詳細資訊，請參閱[存取面板簡介](active-directory-saas-access-panel-introduction.md)。 

## <a name="additional-resources"></a>其他資源

* [如何與 Azure Active Directory 整合 SaaS 應用程式的教學課程清單](active-directory-saas-tutorial-list.md)
* [什麼是搭配 Azure Active Directory 的應用程式存取和單一登入？](manage-apps/what-is-single-sign-on.md)

<!--Image references-->

[1]: ./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_general_04.png

[100]: ./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-cezannehrsoftware-tutorial/tutorial_general_203.png

