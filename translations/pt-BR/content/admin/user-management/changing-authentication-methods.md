---
title: Alterar os métodos de autenticação
intro: 'A qualquer momento, você pode alterar a forma como o {{ site.data.variables.product.prodname_ghe_server }} se autentica com as contas existentes.'
redirect_from:
  - /enterprise/admin/user-management/changing-authentication-methods
versions:
  enterprise-server: '*'
---

As contas de usuário no {{ site.data.variables.product.product_location_enterprise }} são preservadas quando você altera o método de autenticação, e os usuários continuarão fazendo login na mesma conta (desde que não haja alteração nos nomes de usuário).

Se o novo método de autenticação alterar nomes de usuários, serão criadas novas contas. Como administrador, você pode renomear os usuários nas configurações de administração do site ou usando a [a API de administração do usuário](/enterprise/{{currentVersion}}/v3/enterprise-admin/users/#rename-an-existing-user).

Veja outras questões que você deve manter em mente:

* **Senhas:** se você mudar para o uso da autenticação integrada na sua instância, os usuários deverão [definir uma senha](/enterprise/user/articles/how-can-i-reset-my-password/) após a conclusão da mudança.

* **Administradores do site:** privilégios administrativos são [controlados pelo provedor de identidade quando você usa SAML](/enterprise/admin/guides/user-management/using-saml/#saml-attributes) e podem ser [controlados pela associação ao grupo quando você usa LDAP](/enterprise/admin/guides/user-management/using-ldap/#configuring-ldap-with-your-github-enterprise-server-instance).

* **Associação a equipes:** somente o LDAP permite [controlar associações a equipes](/enterprise/admin/guides/user-management/using-ldap/#configuring-ldap-with-your-github-enterprise-server-instance) no servidor do diretório.

* **Suspensão de usuários:** quando você usa o LDAP para fazer a autenticação, o acesso ao {{ site.data.variables.product.prodname_ghe_server }} pode ser controlado pelos _grupos restritos_. Depois de alternar para o LDAP, se os grupos restritos estiverem configurados, os usuários que não estiverem nesses grupos serão suspensos. A suspensão ocorrerá quando eles fizerem login ou durante a próxima sincronização LDAP.

* **Associação a grupos:** quando você usa o LDAP para fazer a autenticação, os usuários passam automaticamente por [suspensão e cancelamento de suspensão](/enterprise/admin/guides/user-management/suspending-and-unsuspending-users) com base em associações a grupos restritos e no status da conta no Active Directory.

* **Autenticação do Git:** o SAML e o CAS dão suporte à autenticação do Git somente em HTTP ou HTTPS usando um [token de acesso pessoal](/articles/creating-an-access-token-for-command-line-use). Não há suporte para a autenticação de senha em HTTP ou HTTPS. Por padrão, o LDAP dá suporte à autenticação do Git com base em senha, mas é recomendável [desabilitar esse método](/enterprise/admin/guides/user-management/using-ldap/#disabling-password-authentication-for-git-operations) e forçar a autenticação via token de acesso pessoal ou chave SSH.

* **Autenticação de API:** o SAML e o CAS dão suporte à autenticação de API somente usando um [token de acesso pessoal](/articles/creating-an-access-token-for-command-line-use). Não há suporte para a autenticação básica.

* **Autenticação de dois fatores:** {{ site.data.reusables.enterprise_user_management.external_auth_disables_2fa }}

* **Autenticação integrada para usuários de fora do provedor de identidade:** você pode convidar os usuários para se autenticarem na {{ site.data.variables.product.product_location_enterprise }} sem adicioná-los ao seu provedor de identidade. Para obter mais informações, consulte "[Permitir a autenticação integrada para usuários de fora do provedor de identidade](/enterprise/{{ currentVersion }}/admin/guides/user-management/allowing-built-in-authentication-for-users-outside-your-identity-provider)".