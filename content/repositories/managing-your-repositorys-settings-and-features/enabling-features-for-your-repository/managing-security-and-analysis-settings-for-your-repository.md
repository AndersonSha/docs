---
title: Managing security and analysis settings for your repository
intro: 'You can control features that secure and analyze the code in your project on {% data variables.product.github %}.'
permissions: People with admin permissions to a repository can manage security and analysis settings for the repository.
redirect_from:
  - /articles/managing-alerts-for-vulnerable-dependencies-in-your-organization-s-repositories
  - /articles/managing-alerts-for-vulnerable-dependencies-in-your-organizations-repositories
  - /articles/managing-alerts-for-vulnerable-dependencies-in-your-organization
  - /github/managing-security-vulnerabilities/managing-alerts-for-vulnerable-dependencies-in-your-organization
  - /github/administering-a-repository/managing-security-and-analysis-settings-for-your-repository
  - /github/administering-a-repository/managing-repository-settings/managing-security-and-analysis-settings-for-your-repository
versions:
  fpt: '*'
  ghes: '*'
  ghec: '*'
type: how_to
topics:
  - Dependabot
  - Alerts
  - Code Security
  - Dependency graph
  - Secret scanning
  - Repositories
shortTitle: Security & analysis
---

{% ifversion dependabot-alerts-enterprise-enablement %}

> [!NOTE]
> When {% data variables.product.prodname_dependabot_alerts %} are enabled or disabled at the enterprise level, it overrides the repository level settings for {% data variables.product.prodname_dependabot_alerts %}. For more information, see [AUTOTITLE](/code-security/dependabot/dependabot-alerts/configuring-dependabot-alerts#managing-dependabot-alerts-for-your-enterprise).

{% endif %}

## About security and analysis settings for your repository

{% data variables.product.github %} offers a number of different security features that you can enable for your repository to
protect your code from vulnerabilities, unauthorized access, and other potential security threats. {% ifversion fpt or ghec %}Many of these features are available for **free for public repositories**.{% endif %}

{% ifversion fpt or ghec %}

## Enabling or disabling security and analysis features for public repositories

You can manage a subset of security and analysis features for public repositories.

At a minimum, you should enable the following for your public repository:

* **{% data variables.product.prodname_dependabot_alerts %}** notify you of security vulnerabilities in your project's dependency network, so that you can update the affected dependency to a more secure version.
* **{% data variables.product.prodname_secret_scanning_caps %}** scans your repository for secrets (such as API keys and tokens) and alerts you if a secret is found, so that you can remove the secret from your repository.
* **Push protection** prevents you (and your collaborators) from introducing secrets to the repository in the first place, by blocking pushes containing supported secrets.
* **{% data variables.product.prodname_code_scanning_caps %}** identifies vulnerabilities and errors in your repository's code, so that you can fix these issues early and prevent a vulnerability or error being exploited by malicious actors.

Other features are permanently enabled for public repositories, such as the dependency graph, which shows you all the libraries and packages that your repository depends upon.

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-settings %}
{% data reusables.repositories.navigate-to-code-security-and-analysis %}
1. Under "{% data variables.product.UI_advanced_security %}", to the right of the feature, click **Disable** or **Enable**.

{% endif %}

## Enabling or disabling security and analysis features{% ifversion fpt or ghec %} for private repositories{% endif %}

You can manage the security and analysis features for your {% ifversion fpt or ghec %}private or internal {% endif %}repository. If your enterprise or organization has a license for {% ifversion ghas-products %}{% data variables.product.prodname_GH_code_security %} or {% data variables.product.prodname_GH_secret_protection %}{% else %}{% data variables.product.prodname_GHAS %}{% endif %}, then extra options are available. {% data reusables.advanced-security.more-info-ghas %}

{% data reusables.security.security-and-analysis-features-enable-read-only %}

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-settings %}
{% data reusables.repositories.navigate-to-code-security-and-analysis %}
1. Under "{% data variables.product.UI_advanced_security %}", to the right of the feature, click **Disable** or **Enable**. The control for "{% data variables.product.prodname_cs_and_sp %}" is disabled if your {% data variables.enterprise.enterprise_or_org %} has no available licenses.

   > [!NOTE]
   > If you disable {% data variables.product.prodname_cs_and_sp %}, dependency review, {% data variables.secret-scanning.user_alerts %} and {% data variables.product.prodname_code_scanning %} are disabled. Any workflows, SARIF uploads, or API calls for {% data variables.product.prodname_code_scanning %} will fail. If {% data variables.product.prodname_code_security %} is re-enabled, {% data variables.product.prodname_code_scanning %} will return to its previous state.

## Granting access to security alerts

{% data variables.product.github %} security alerts are automated notifications that inform you when vulnerabilities are found in your repository's dependencies or code. They prompt you to review and remediate these issues, helping to keep your project secure.

You can find security alerts from {% data variables.product.prodname_dependabot %}, {% data variables.product.prodname_secret_scanning_caps %}, and {% data variables.product.prodname_code_scanning_caps %} under your repository's **Security** tab.

Security alerts for a repository are visible to people with write, maintain, or admin access to the repository and, when the repository is owned by an organization, organization owners. You can give additional teams and people access to the alerts.

> [!NOTE]
> Organization owners and repository administrators can only grant access to view security alerts, such as {% data variables.secret-scanning.alerts %}, to people or teams who have write access to the repo.

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-settings %}
{% data reusables.repositories.navigate-to-code-security-and-analysis %}
1. Under "Access to alerts", in the search field, start typing the name of the person or team you'd like to find, then click a name in the list of matches.
1. Click **Save changes**.

## Removing access to security alerts

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-settings %}
{% data reusables.repositories.navigate-to-code-security-and-analysis %}
1. Under "Access to alerts", to the right of the person or team whose access you'd like to remove, click {% octicon "x" aria-label="Revoke USER's vulnerability access " %}.

     ![Screenshot of the list of users with access to alerts. To the right of @octocat, an x icon is outlined in dark orange.](/assets/images/help/repository/security-and-analysis-security-alerts-username-x.png)
1. Click **Save changes**.

## Further reading

* [AUTOTITLE](/code-security/getting-started/securing-your-repository)
* [AUTOTITLE](/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization)
