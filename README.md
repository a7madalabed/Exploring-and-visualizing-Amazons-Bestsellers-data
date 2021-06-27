# Exploring-and-visualizing-Amazons-Bestsellers-data
A brief look into Amazon's bestsellers between 2009 &amp; 2019.
{
 "cells": [
  {
   "cell_type": "markdown",
   "id": "816ed6fe",
   "metadata": {},
   "source": [
    "# Amazon Top 50 Bestselling Books 2009 - 2019\n",
    "\n",
    "One of the most important steps of any data science project is to exploring and visualize the data you have collected and cleaned to gain insight.\n",
    "\n",
    "In this simple Notebook we are going to dive into Amazon Top 50 Bestselling Books 2009 - 2019 dataset, explore and visualize the dataset and see what insights we can collect.\n",
    "\n",
    "But first let's import the libraries we will work with :\n",
    "1. _Numpy_ \n",
    "2. _Pandas_\n",
    "3. _Matplotlib_\n",
    "4. _Seaborn_"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "b326401b",
   "metadata": {},
   "outputs": [],
   "source": [
    "import numpy as np\n",
    "import pandas as pd\n",
    "%matplotlib inline\n",
    "import matplotlib as mpl\n",
    "import matplotlib.pyplot as plt\n",
    "mpl.rc('axes', labelsize=14)\n",
    "mpl.rc('xtick', labelsize=12)\n",
    "mpl.rc('ytick', labelsize=12)\n",
    "plt.style.use('ggplot')\n",
    "import seaborn as sns\n",
    "sns.set_palette('husl')"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "0a855742",
   "metadata": {},
   "source": [
    "We then load the dataset CSV file using Pandas function: **read_csv**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "id": "3ba41992",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Name</th>\n",
       "      <th>Author</th>\n",
       "      <th>User Rating</th>\n",
       "      <th>Reviews</th>\n",
       "      <th>Price</th>\n",
       "      <th>Year</th>\n",
       "      <th>Genre</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>10-Day Green Smoothie Cleanse</td>\n",
       "      <td>JJ Smith</td>\n",
       "      <td>4.7</td>\n",
       "      <td>17350</td>\n",
       "      <td>8</td>\n",
       "      <td>2016</td>\n",
       "      <td>Non Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>11/22/63: A Novel</td>\n",
       "      <td>Stephen King</td>\n",
       "      <td>4.6</td>\n",
       "      <td>2052</td>\n",
       "      <td>22</td>\n",
       "      <td>2011</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>12 Rules for Life: An Antidote to Chaos</td>\n",
       "      <td>Jordan B. Peterson</td>\n",
       "      <td>4.7</td>\n",
       "      <td>18979</td>\n",
       "      <td>15</td>\n",
       "      <td>2018</td>\n",
       "      <td>Non Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>1984 (Signet Classics)</td>\n",
       "      <td>George Orwell</td>\n",
       "      <td>4.7</td>\n",
       "      <td>21424</td>\n",
       "      <td>6</td>\n",
       "      <td>2017</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>5,000 Awesome Facts (About Everything!) (Natio...</td>\n",
       "      <td>National Geographic Kids</td>\n",
       "      <td>4.8</td>\n",
       "      <td>7665</td>\n",
       "      <td>12</td>\n",
       "      <td>2019</td>\n",
       "      <td>Non Fiction</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                                                Name  \\\n",
       "0                      10-Day Green Smoothie Cleanse   \n",
       "1                                  11/22/63: A Novel   \n",
       "2            12 Rules for Life: An Antidote to Chaos   \n",
       "3                             1984 (Signet Classics)   \n",
       "4  5,000 Awesome Facts (About Everything!) (Natio...   \n",
       "\n",
       "                     Author  User Rating  Reviews  Price  Year        Genre  \n",
       "0                  JJ Smith          4.7    17350      8  2016  Non Fiction  \n",
       "1              Stephen King          4.6     2052     22  2011      Fiction  \n",
       "2        Jordan B. Peterson          4.7    18979     15  2018  Non Fiction  \n",
       "3             George Orwell          4.7    21424      6  2017      Fiction  \n",
       "4  National Geographic Kids          4.8     7665     12  2019  Non Fiction  "
      ]
     },
     "execution_count": 2,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df = pd.read_csv(\"bestsellers with categories.csv\")\n",
    "df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "id": "2704217d",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 550 entries, 0 to 549\n",
      "Data columns (total 7 columns):\n",
      " #   Column       Non-Null Count  Dtype  \n",
      "---  ------       --------------  -----  \n",
      " 0   Name         550 non-null    object \n",
      " 1   Author       550 non-null    object \n",
      " 2   User Rating  550 non-null    float64\n",
      " 3   Reviews      550 non-null    int64  \n",
      " 4   Price        550 non-null    int64  \n",
      " 5   Year         550 non-null    int64  \n",
      " 6   Genre        550 non-null    object \n",
      "dtypes: float64(1), int64(3), object(3)\n",
      "memory usage: 30.2+ KB\n"
     ]
    }
   ],
   "source": [
    "df.info()"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "c6ec17cb",
   "metadata": {},
   "source": [
    "By using another one of the many usefull functions of the Pandas library, **the info() fuction** we can get an overview of how much missing data we have if any, what's the type of each column(feature) and how much rows and columns our data have.\n",
    "\n",
    "In this particular dataset for example:\n",
    "1. there are no missing data.\n",
    "2. the dataset contains 550 rows and 7 columns."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "id": "ffa620bd",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>User Rating</th>\n",
       "      <th>Reviews</th>\n",
       "      <th>Price</th>\n",
       "      <th>Year</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>count</th>\n",
       "      <td>550.000000</td>\n",
       "      <td>550.000000</td>\n",
       "      <td>550.000000</td>\n",
       "      <td>550.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>mean</th>\n",
       "      <td>4.618364</td>\n",
       "      <td>11953.281818</td>\n",
       "      <td>13.100000</td>\n",
       "      <td>2014.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>std</th>\n",
       "      <td>0.226980</td>\n",
       "      <td>11731.132017</td>\n",
       "      <td>10.842262</td>\n",
       "      <td>3.165156</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>min</th>\n",
       "      <td>3.300000</td>\n",
       "      <td>37.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>2009.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>25%</th>\n",
       "      <td>4.500000</td>\n",
       "      <td>4058.000000</td>\n",
       "      <td>7.000000</td>\n",
       "      <td>2011.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50%</th>\n",
       "      <td>4.700000</td>\n",
       "      <td>8580.000000</td>\n",
       "      <td>11.000000</td>\n",
       "      <td>2014.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>75%</th>\n",
       "      <td>4.800000</td>\n",
       "      <td>17253.250000</td>\n",
       "      <td>16.000000</td>\n",
       "      <td>2017.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>max</th>\n",
       "      <td>4.900000</td>\n",
       "      <td>87841.000000</td>\n",
       "      <td>105.000000</td>\n",
       "      <td>2019.000000</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "       User Rating       Reviews       Price         Year\n",
       "count   550.000000    550.000000  550.000000   550.000000\n",
       "mean      4.618364  11953.281818   13.100000  2014.000000\n",
       "std       0.226980  11731.132017   10.842262     3.165156\n",
       "min       3.300000     37.000000    0.000000  2009.000000\n",
       "25%       4.500000   4058.000000    7.000000  2011.000000\n",
       "50%       4.700000   8580.000000   11.000000  2014.000000\n",
       "75%       4.800000  17253.250000   16.000000  2017.000000\n",
       "max       4.900000  87841.000000  105.000000  2019.000000"
      ]
     },
     "execution_count": 4,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.describe()"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "045c55e9",
   "metadata": {},
   "source": [
    "By using the **describe function** we can get some insight to things like the mean user rating and the mean price for a bestseller book.\n",
    "\n",
    "For example, you should be able to notice that the lowest rated best seller book got a mere ***3.3*** user rating."
   ]
  },
  {
   "cell_type": "markdown",
   "id": "0644c3f8",
   "metadata": {},
   "source": [
    "# Now let's visualize the dataset"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "id": "bdd139d2",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 1440x1080 with 4 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "%matplotlib inline\n",
    "import matplotlib.pyplot as plt\n",
    "df.hist(bins=50, figsize=(20,15))\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "1e8fd2a9",
   "metadata": {},
   "source": [
    "**From the graphs above we can see that:**\n",
    "1. most of the user ratings ranges between 4.6 and 4.8.\n",
    "2. most of the books got less than 20000 reviews.\n",
    "3. most of prices ranges from 10 to 20 dollars.\n",
    "\n",
    "**important notes:** \n",
    "1. books prices listed as zero's are probably just filled by zero's instead of NA for convenience but they should be dealt with.\n",
    "2. Also books with prices like 80 and 100 dollars should be investigated if they are outliers or not."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "id": "af09fe5c",
   "metadata": {},
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "*c* argument looks like a single numeric RGB or RGBA sequence, which should be avoided as value-mapping will have precedence in case its length matches with *x* & *y*.  Please use the *color* keyword-argument or provide a 2-D array with a single row if you intend to specify the same RGB or RGBA value for all points.\n"
     ]
    },
    {
     "data": {
      "text/plain": [
       "<AxesSubplot:xlabel='User Rating', ylabel='Genre'>"
      ]
     },
     "execution_count": 15,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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TFFRkUlOTg5ZTcc60Xu0d+9eM2TIEP/BGTNmzDB5eXlhr6umpsYkJSWZ2bNnd1gtRwtkTHfUuA9kmeEY94HUFe5x3xaC6zSzYMECk5qaatLT080tt9xiysvLzdatW016enqLth35AQ6kri1btpiMjAyTmppqxowZY955551Toq758+eblJQUk5aWZm688Ubz8ccfh7yuI45+j46tq6SkxKSlpZmUlBSTk5Nj9u/fH/a6nn32WTNgwACTnp7e7G/fvn1hretEbTpKa3WFY9wHUlc4x31buKwJAMAq7OMCAFiF4AIAWIXgAgBYheACAFiF4AIAWIXgAsIsPj5e+/btazavqKhI2dnZIVnerl279JOf/ERer9f/N2LECGVnZwf0H1+feeYZFRcXS5JmzZqlV155JSR1AifCuQqB7yCPx6MVK1b4p40xKigo0MyZM/Xkk0+2+ti3335b5513niTp7rvvDmmdwPEQXMApbvv27crPz1dDQ4OMMcrIyFBWVpYk6Y9//KP+8Y9/yHEc9enTR9OmTdP3v/99ZWdnq1u3bvrss880fvz4Ntfe6uvrVVlZqZ49e0rynfz1t7/9rQ4ePKg9e/ZowIABeuqpp7Rs2TJt27ZNhYWFioiI0Lp169S/f39NnDhRAwcOVE5Ojt58801VVlbqlltu0Q033KCmpiYVFhbqn//8p7p06aKEhARt375d8+bNC/lrh9MTwQWc4p5//nklJSUpJydHe/bs0WOPPabx48dr5cqV+vjjj7V06VJFRkZq8eLFmjp1qp577jlJUteuXbV27drj9nnk/HSO46iqqkrdunXTyJEjlZOTI0lasmSJRo8eLa/Xq8OHD2vs2LEqKSlRVlaWioqKlJWVpREjRmjdunX+PhsaGtS9e3ctWrRI27Zt0/jx43Xttddq+fLl+te//qXVq1fL5XLptttuC/2LhtMawQWE2fHO8u44jv9M7yNGjND999+vrVu3asiQIZo6darcbrdef/11lZaW6tprr/U/5tChQ/4+Lr744hMu8+hNhW+88YZyc3M1bNgwde7cWZKUm5urN998U88995w+//xzVVZWqra2ts3nMnz4cEnSBRdcoIaGBtXW1mr9+vXyer3+6zllZmaytoVvheACwqx79+763//+px49evjnVVVV+S9qOWzYML366qvatGmTNm/erDlz5ujll1+W4zj+zXGSb43n6DPbB3qm+CuuuEI333yz7r77bq1Zs0ZxcXG699571dTUpKuvvlq//OUvVVFREdAlLY6E05EwNsYoMrL510woL72C7wZGEBBmV155pebNm+e/Dlh1dbWWL1/uvyrufffdp7Vr1yo1NVXTpk1TXFycysvLdfnll2vZsmU6cOCAJN8RflOmTAmqhl/96lfq3Lmznn76aUm+y1rccccduuaaayRJH374oZqamiRJERERamxsDLjvoUOHauXKlWpoaFBjY6OWL18eVI3AEaxxAWGWn5+vxx9/XKNGjVJERIQkyev1asyYMZKk22+/Xfn5+Vq8eLEiIiKUnJysSy65RBdffLF2796t66+/Xi6XS71799bjjz8eVA1RUVF66KGHdMsttygjI0P33HOP7rjjDsXGxiouLk6XXHKJysvLJUlJSUl68skndfjw4YD6Hjt2rHbs2KHRo0crNjZWffv2VUxMTFB1ApLE2eEBhNTGjRtVVVUlr9crSSooKFCnTp065BL1OD0RXABCavfu3crLy9PevXvlOI4GDBighx9+WF26dAl3abAUwQUAsAoHZwAArEJwAQCsQnABAKxCcAEArEJwAQCs8n8qp9mWWbVKBwAAAABJRU5ErkJggg==\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "df.plot(kind=\"scatter\", x=\"User Rating\", y=\"Genre\", alpha=0.5)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "53881996",
   "metadata": {},
   "source": [
    "The graph above shows that the probability for a Non Fiction book to get a user rating less than 4 are less likely compared to their counterparts that got a user rating average as low as 3.3."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "id": "dfcc25b2",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Non Fiction    310\n",
       "Fiction        240\n",
       "Name: Genre, dtype: int64"
      ]
     },
     "execution_count": 7,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df[\"Genre\"].value_counts()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "id": "1312ab55",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0.5, 1.0, 'Genre Pie Chart for the top 10 Bestselling Books on Amazon (2009-2019)')"
      ]
     },
     "execution_count": 8,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 576x576 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "pie = [310, 240]\n",
    "sns.set_palette(\"husl\")\n",
    "plt.figure(figsize=(8,8))\n",
    "plt.pie(pie ,labels=['Fiction','Non Fiction'],autopct='%.1f%%',shadow=True,startangle=90)\n",
    "plt.title('Genre Pie Chart for the top 10 Bestselling Books on Amazon (2009-2019)')"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "1e0d355e",
   "metadata": {},
   "source": [
    "**As you can see, even thought Non Fiction books are rated better than Fiction books it doesn't mean that they are more popular.**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "id": "bb35d6e5",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Jeff Kinney                           12\n",
       "Suzanne Collins                       11\n",
       "Gary Chapman                          11\n",
       "Rick Riordan                          11\n",
       "American Psychological Association    10\n",
       "                                      ..\n",
       "Michael Lewis                          1\n",
       "Michael Pollan                         1\n",
       "George W. Bush                         1\n",
       "Dave Ramsey                            1\n",
       "Daniel H. Pink                         1\n",
       "Name: Author, Length: 248, dtype: int64"
      ]
     },
     "execution_count": 9,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df[\"Author\"].value_counts()"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "a52da4bf",
   "metadata": {},
   "source": [
    "By using the value counts function from the pandas library we can get an overview of how many books each auther has in the list.\n",
    "\n",
    "For example, **Jeff kinney** has the most books in the bestsellers dataset with 12 books folowed by **Suzanne Collins, Gary Chapman and Rick Riordan**."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "id": "46573a24",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Name</th>\n",
       "      <th>Author</th>\n",
       "      <th>User Rating</th>\n",
       "      <th>Reviews</th>\n",
       "      <th>Price</th>\n",
       "      <th>Year</th>\n",
       "      <th>Genre</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>264</th>\n",
       "      <td>Percy Jackson and the Olympians Paperback Boxe...</td>\n",
       "      <td>Rick Riordan</td>\n",
       "      <td>4.8</td>\n",
       "      <td>548</td>\n",
       "      <td>2</td>\n",
       "      <td>2010</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>343</th>\n",
       "      <td>The Blood of Olympus (The Heroes of Olympus (5))</td>\n",
       "      <td>Rick Riordan</td>\n",
       "      <td>4.8</td>\n",
       "      <td>6600</td>\n",
       "      <td>11</td>\n",
       "      <td>2014</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>406</th>\n",
       "      <td>The House of Hades (Heroes of Olympus, Book 4)</td>\n",
       "      <td>Rick Riordan</td>\n",
       "      <td>4.8</td>\n",
       "      <td>6982</td>\n",
       "      <td>14</td>\n",
       "      <td>2013</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>418</th>\n",
       "      <td>The Last Olympian (Percy Jackson and the Olymp...</td>\n",
       "      <td>Rick Riordan</td>\n",
       "      <td>4.8</td>\n",
       "      <td>4628</td>\n",
       "      <td>7</td>\n",
       "      <td>2009</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>428</th>\n",
       "      <td>The Lost Hero (Heroes of Olympus, Book 1)</td>\n",
       "      <td>Rick Riordan</td>\n",
       "      <td>4.8</td>\n",
       "      <td>4506</td>\n",
       "      <td>14</td>\n",
       "      <td>2010</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>432</th>\n",
       "      <td>The Mark of Athena (Heroes of Olympus, Book 3)</td>\n",
       "      <td>Rick Riordan</td>\n",
       "      <td>4.8</td>\n",
       "      <td>6247</td>\n",
       "      <td>10</td>\n",
       "      <td>2012</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>456</th>\n",
       "      <td>The Red Pyramid (The Kane Chronicles, Book 1)</td>\n",
       "      <td>Rick Riordan</td>\n",
       "      <td>4.6</td>\n",
       "      <td>2186</td>\n",
       "      <td>12</td>\n",
       "      <td>2010</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>458</th>\n",
       "      <td>The Serpent's Shadow (The Kane Chronicles, Boo...</td>\n",
       "      <td>Rick Riordan</td>\n",
       "      <td>4.8</td>\n",
       "      <td>2091</td>\n",
       "      <td>12</td>\n",
       "      <td>2012</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>463</th>\n",
       "      <td>The Son of Neptune (Heroes of Olympus, Book 2)</td>\n",
       "      <td>Rick Riordan</td>\n",
       "      <td>4.8</td>\n",
       "      <td>4290</td>\n",
       "      <td>10</td>\n",
       "      <td>2011</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>469</th>\n",
       "      <td>The Throne of Fire (The Kane Chronicles, Book 2)</td>\n",
       "      <td>Rick Riordan</td>\n",
       "      <td>4.7</td>\n",
       "      <td>1463</td>\n",
       "      <td>10</td>\n",
       "      <td>2011</td>\n",
       "      <td>Fiction</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                                                  Name        Author  \\\n",
       "264  Percy Jackson and the Olympians Paperback Boxe...  Rick Riordan   \n",
       "343   The Blood of Olympus (The Heroes of Olympus (5))  Rick Riordan   \n",
       "406     The House of Hades (Heroes of Olympus, Book 4)  Rick Riordan   \n",
       "418  The Last Olympian (Percy Jackson and the Olymp...  Rick Riordan   \n",
       "428          The Lost Hero (Heroes of Olympus, Book 1)  Rick Riordan   \n",
       "432     The Mark of Athena (Heroes of Olympus, Book 3)  Rick Riordan   \n",
       "456      The Red Pyramid (The Kane Chronicles, Book 1)  Rick Riordan   \n",
       "458  The Serpent's Shadow (The Kane Chronicles, Boo...  Rick Riordan   \n",
       "463     The Son of Neptune (Heroes of Olympus, Book 2)  Rick Riordan   \n",
       "469   The Throne of Fire (The Kane Chronicles, Book 2)  Rick Riordan   \n",
       "\n",
       "     User Rating  Reviews  Price  Year    Genre  \n",
       "264          4.8      548      2  2010  Fiction  \n",
       "343          4.8     6600     11  2014  Fiction  \n",
       "406          4.8     6982     14  2013  Fiction  \n",
       "418          4.8     4628      7  2009  Fiction  \n",
       "428          4.8     4506     14  2010  Fiction  \n",
       "432          4.8     6247     10  2012  Fiction  \n",
       "456          4.6     2186     12  2010  Fiction  \n",
       "458          4.8     2091     12  2012  Fiction  \n",
       "463          4.8     4290     10  2011  Fiction  \n",
       "469          4.7     1463     10  2011  Fiction  "
      ]
     },
     "execution_count": 10,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "new_df = df.drop_duplicates('Name')\n",
    "new_df[new_df['Author']=='Rick Riordan']"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "d85f5bec",
   "metadata": {},
   "source": [
    "If we dive a little deeper into each author list we can see some hidden details about their books.\n",
    "\n",
    "Here we accessed the books written by Rick Riordan and we were able to notice that most of the books are from the **Heroes of Olympus** book series."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "id": "4bc11ad6",
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "image/png": "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TXNWzCQDCPZnDCIiIiIiJ6JfS5yBk4ArTNO8AsgErgfUo4aIiIiIpL3+7sf5VuAQTi8b64HXcBoQioiIiIikNcO2B0T1YbuqqirVMYiIiIjIIFdeXm5095pGDhQRERERiYMSZxERERGROChxFhERERGJgxJnEREREZE4KHEWEREREYmDEmcRERERkTgocRYRERERiYMSZxERERGROChxFhERERGJgxJnEREREZE4KHEWEREREYmDEmcRERERkTgocRYRERERiYMSZxERERGROChxFhERERGJgxJnEREREZE4KHEWEREREYmDEmcRERERkTgocRYRERERiYMSZxERERGROChxFhERERGJgxJnEREREZE4KHEWEREREYmDEmcRERERkTgocRYRERERiYMSZxERERGROChxFhERERGJgxJnEREREZE4KHEWEREREYmDEmcRERERkTgocRYRERERiYMSZxERERGROChxFhERERGJgxJnEREREZE4KHEWEREREYmDEmcRERERkTgocRYRERERiYMSZxERERGROChxFhERERGJgxJnEREREZE4KHEWEREREYmDEmcRERERkTgocRYRERERiYMSZxERERGROChxFhERERGJQ0YyV26apgHcA2ywLOvnpmm6gV8AF0a3/XPLsv6QzBhERERERBIhaSXOpmlOB54HPhwz+fPAFOAkYCHwFdM0FyUrBhERERGRRElmVY0vAX8C/hkz7TLgbsuyQpZl1QN/Bz6ZxBhERERERBIiaVU1LMu6HsA0zfNjJo8B9sQ83wvMSlYMIiIiIiKJktQ6zl1wAXbMcwMIdzWjaZrXAdcBWJZFeXl58qMTERERkaHOxslRj9HfvWpUArEZcDlOqfMxLMu6w7KsBZZlLcAJPiUP0zTXpHL72mfts/ZZ+6t91j5rn7XP2ud+f3Spv0ucHwWuNU3zcSAX+BjwH/0cg4iIiIhIr/V34vx7YCLwFpAJ/NGyrJf7OQYRERERkV5LeuJsWdbVMf+HgK8ke5sJdkeqA0gB7fPQMNT2eajtL2ifhwrt89CgfU4Dhm3bx59LRERERGSI05DbIiIiIiJx6O86zilnmuYngW/idDXSBnwZWEs3Q4GbpjkZuBMoBlqAT1mWtTk6nPgPgI8CrcBrwNcsy/L37x4dX2/3OWa5a4HLLMv6YKdp3wA8wHPAly3L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\n",
      "text/plain": [
       "<Figure size 864x432 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "books = df.groupby(['Year','Genre']).count().unstack()['Name']\n",
    "\n",
    "fig,axes=plt.subplots(1,1,figsize=(12,6))\n",
    "sns.set_style('white')\n",
    "axes.plot(books,markersize=5,markerfacecolor='grey',marker='o')\n",
    "axes.set_xlabel('Year')\n",
    "axes.set_ylabel('Number Of Entries')\n",
    "axes.set_xticks(books.index)\n",
    "axes.set_ylim(10,40)\n",
    "axes.spines['right'].set_color('none')\n",
    "axes.spines['top'].set_color('none')\n",
    "axes.legend(books)\n",
    "axes.set_title('Fiction Vs. Non Fiction Books In The Bestsellers List (2009-2019)',fontdict={'size':15})\n",
    "plt.grid(0)\n",
    "\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "aba94a02",
   "metadata": {},
   "source": [
    "We can also use data visualization to see that Non Fiction enteries had been more common than Fiction entries through the years 2009-2019.\n",
    "\n",
    "The only except to this rule is the year 2014."
   ]
  },
  {
   "cell_type": "markdown",
   "id": "4015a649",
   "metadata": {},
   "source": [
    "# Thanks for reading.\n",
    "\n",
    "## By the end of this I hope that:\n",
    "### 1. this was a brief and good introduction to the power of data exploration and data visualization.\n",
    "### 2. The reader had learned at least one new thing from reading this jupyter notebook."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "f16d92c3",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.8"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
