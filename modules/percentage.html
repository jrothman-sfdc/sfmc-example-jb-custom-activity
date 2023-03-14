const { Activity } = require('s4s-activity-sdk-nodejs');

class CustomActivity extends Activity {
  async execute() {
    // Retrieve inputs
    const percentage = this.settings.percentage; // Percentage for each path
    const limits = this.settings.limits; // Limits for each path
    const totalLimit = this.settings.totalLimit; // Total limit for all paths
    const pathCount = Object.keys(percentage).length; // Count number of paths

    // Calculate limits per path based on total limit and percentages
    const pathLimits = {};
    let remainingLimit = totalLimit;
    for (let i = 0; i < pathCount - 1; i++) {
      const pathPercentage = percentage[i] / 100;
      const pathLimit = Math.floor(remainingLimit * pathPercentage);
      pathLimits[i] = pathLimit;
      remainingLimit -= pathLimit;
    }
    pathLimits[pathCount - 1] = remainingLimit;

    // Retrieve incoming contacts
    const contacts = this.payload.contacts;

    // Split contacts into paths based on percentage and limits
    const pathContacts = {};
    for (let i = 0; i < pathCount; i++) {
      pathContacts[i] = [];
    }
    for (const contact of contacts) {
      const path = this._getRandomPath(pathCount, percentage);
      if (pathContacts[path].length < pathLimits[path]) {
        pathContacts[path].push(contact);
      }
    }

    // Output contacts for each path
    for (let i = 0; i < pathCount; i++) {
      this.output(i, pathContacts[i]);
    }
  }

  // Helper function to randomly select a path based on percentage
  _getRandomPath(pathCount, percentage) {
    const totalPercentage = Object.values(percentage).reduce((a, b) => a + b);
    let remainingPercentage = totalPercentage;
    let path;
    while (remainingPercentage > 0 && !path) {
      const random = Math.random() * remainingPercentage;
      for (let i = 0; i < pathCount; i++) {
        if (random < percentage[i]) {
          path = i;
          break;
        }
        random -= percentage[i];
      }
      remainingPercentage -= percentage[path];
      if (pathCount === 1) {
        break;
      }
      if (path !== undefined && percentage[path] === 0) {
        path = undefined;
      }
    }
    return path;
  }
}

module.exports = CustomActivity;
