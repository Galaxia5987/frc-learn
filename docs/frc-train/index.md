# Setup FRC Train

FRC Train is an interactive github repo that you can fork, and complete interactive coding tasks in FRC. All tasks are opened as Pull Requests.

### Completing a task

After setting up your own fork of FRCTrain(check [FRC Train Setup Utility](#frc-train-setup-utility) on how to do this), you will see a number of open Pull Requests. Each task will be written in it's Pull Request's description.

To complete a task, you will need to checkout the respective task branch in your code editor, commit your changes, and push.

Automated tests will then be run, to check if you completed the task at a basic level.

!!! note
    Not everything is checked in the automated tests, and thus, the task will only be marked as finished(done automatically) if someone approves your Pull Request and the tests are passing.

## FRC Train Setup Utility

Please follow and read the steps below carefully to setup your FRCTrain environment.

### Fork the repository

Click the below button to create your own version of FRCTrain. Make sure to select **your own profile** and **not** Galaxia5987 or similar.

[Fork Repository](https://github.com/Galaxia5987/frc-train/fork){.md-button .md-button--primary }

### Setup Environment

After forking the repository, you will need to use the following automated tool to setup the repository.

For that, you will need to generate a Github Personal Access Token.

To generate a token, please [click here](https://github.com/settings/personal-access-tokens/new?name=FRC+Train+Token&expires_in=100&description=Make%20sure%20to%20limit%20this%20token%20to%20only%20the%20FRCTrain%20repository%20you%20just%20forked%21%21%21&contents=write&actions=write&pull_requests=write&workflows=write&administration=write&secrets=write).

!!! warning
    Make sure to click "Only select repositories" and choose the repository you just forked. It should be `YourName/frc-train` and **not** `Galaxia5987/frc-train` or similar.

After getting a token, enter it below and click "Setup Environment"

<form id="configForm" style="max-width: 500px;">
  
  <div style="margin-bottom: 1.5rem;">
    <label for="githubToken" style="display: block; font-weight: 700; margin-bottom: 0.4rem;">
      GitHub Token <span style="color: var(--md-typeset-a-color, red);">*</span>
    </label>
    <input type="password" id="githubToken" name="githubToken" required 
           placeholder="github_pat_..." 
           pattern="^github_pat_[a-zA-Z0-9]{22}_[a-zA-Z0-9]{59}$"
           title="Must be a fine-grained GitHub token starting with github_pat_ followed by the correct number of characters."
           style="width: 100%; padding: 0.5rem; border: 1px solid var(--md-default-fg-color--lighter); border-radius: 0.1rem; background: var(--md-default-bg-color); color: var(--md-default-fg-color); outline: none;">
  </div>

  <details class="note" style="margin-bottom: 1.5rem;">
    <summary>Advanced Settings</summary>
    <div style="margin-top: 1rem;">
      <label for="repoPath" style="display: block; font-weight: 700; margin-bottom: 0.4rem;">
        Repository Path
      </label>
      <input type="text" id="repoPath" name="repoPath" 
             placeholder="e.g., AdarWa/frc-train" 
             pattern="^[a-zA-Z0-9-]+\/[a-zA-Z0-9_.-]+$"
             title="Must be in the format 'owner/repo'."
             style="width: 100%; padding: 0.5rem; border: 1px solid var(--md-default-fg-color--lighter); border-radius: 0.1rem; background: var(--md-default-bg-color); color: var(--md-default-fg-color); outline: none;">
    </div>
  </details>

  <button type="submit" class="md-button md-button--primary">Setup Environment</button>

</form>

<script>
  document.getElementById('configForm').addEventListener('submit', async function(event) {
    event.preventDefault(); 

    const formData = new FormData(event.target);
    const token = formData.get('githubToken');
    const repo = formData.get('repoPath');

    const tokenRegex = /^github_pat_[a-zA-Z0-9]{22}_[a-zA-Z0-9]{59}$/;
    const repoRegex = /^[a-zA-Z0-9-]+\/[a-zA-Z0-9_.-]+$/;

    if (!tokenRegex.test(token)) {
      alert("Validation Error: Invalid GitHub token format. Please use a fine-grained personal access token.");
      return;
    }

    if (repo && !repoRegex.test(repo)) {
      alert("Validation Error: Invalid repository path. It must be in the 'owner/repo' format.");
      return;
    }
    
    const payload = {
      token: token,
      repo: repo || undefined 
    };

    try {
      const response = await fetch('https://g6lagww1d4.execute-api.eu-north-1.amazonaws.com/default/frc-train-setup', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(payload)
      });

      if (response.ok) {
        alert("Success: Request completed.");
      } else {
        alert(`Error: Server returned status ${response.status}`);
      }
    } catch (error) {
      alert(`Network Error: ${error.message}`);
    }
  });
</script>

!!! note
    If you wish, you can also run the setup script locally, see [this](https://github.com/Galaxia5987/frc-train/tree/main/setup).