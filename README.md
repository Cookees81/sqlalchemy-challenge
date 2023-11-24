# sqlalchemy-challenge
Found solution for plotting x-axis from matplotlib.org site path: Ticks/Placing date ticks using recurrence rules.
import datetime

import matplotlib.pyplot as plt
import numpy as np

from matplotlib.dates import (YEARLY, DateFormatter, RRuleLocator, drange,
                              rrulewrapper)

# Fixing random state for reproducibility
np.random.seed(19680801)


# tick every 5th easter
rule = rrulewrapper(YEARLY, byeaster=1, interval=5)
loc = RRuleLocator(rule)
formatter = DateFormatter('%m/%d/%y')
date1 = datetime.date(1952, 1, 1)
date2 = datetime.date(2004, 4, 12)
delta = datetime.timedelta(days=100)

dates = drange(date1, date2, delta)
s = np.random.rand(len(dates))  # make up some random y values


fig, ax = plt.subplots()
plt.plot(dates, s, 'o')
ax.xaxis.set_major_locator(loc)
ax.xaxis.set_major_formatter(formatter)
ax.xaxis.set_tick_params(rotation=30, labelsize=10)

plt.show()