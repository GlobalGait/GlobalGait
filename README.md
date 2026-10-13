# Global Gait dashboard

A worldwide study of pedestrian gait speed by the biomechanics community.

This repository holds the website version of the Global Gait dashboard. It is a static page: there is no server and no database.

- `index.html` is the dashboard.
- `data/globalgait-data.json` holds the data. It is encrypted with a project password, so it can sit in a public repository.

## Opening the dashboard

Go to the GitHub Pages address of this repository and enter the project password. The page remembers the password until you close the browser tab.

## Adding new sessions

Researchers export a JSON file from the Global Gait tool and send it to the data manager. The data manager adds it to the website:

1. Open the dashboard and enter the password.
2. Drop the new JSON files on "Add sessions". They appear straight away, but only in your browser.
3. Click **Download data file**. Keep the same password, or type a new one to change it.
4. In this repository, open the `data` folder and choose **Add file → Upload files**.
5. Upload the downloaded `globalgait-data.json`. It replaces the old file.
6. Click **Commit changes**.

The website updates within a minute or two. GitHub keeps every earlier version of the data file in the history.

Removing a session works the same way: click **Remove** in the sessions table, download the data file and upload it again.

## Making the data public

When the study is ready to share, download the data file with an empty password field. Tick **Leave out researcher names** if those should not be public. Then remove the `noindex` line from `index.html` and the rule in `robots.txt` so search engines can find the page.

## Security

The data are encrypted with AES-256-GCM. The key is derived from the password with PBKDF2-SHA256 (600,000 iterations), and everything runs in the browser.

- **Strength:** the protection is as strong as the password, so use a long one.
- **Changing the password:** a new password does not protect copies of the file that were downloaded earlier.
- **History:** older versions of the data file stay in the git history, and they still open with the old password.
