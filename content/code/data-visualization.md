---
title: "Data Visualization Tools"
date: 2023-08-15
draft: false
tags: ["python", "data-visualization", "matplotlib"]
summary: "A collection of Python functions for creating publication-quality data visualizations"
---

# Data Visualization Tools

This page provides a collection of Python functions that I frequently use to create publication-quality data visualizations. Feel free to use and adapt these code snippets for your own research.

## Basic Plot with Custom Styling

Here's a basic example of creating a well-styled plot with Matplotlib:

```python
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns

# Set the style
plt.style.use('seaborn-whitegrid')
sns.set_context("paper")

def create_styled_plot(x, y, title=None, xlabel=None, ylabel=None, color='#1f77b4'):
    """
    Create a nicely styled plot with custom formatting.
    
    Parameters:
    -----------
    x, y : array-like
        The data to plot
    title, xlabel, ylabel : str
        Plot labels
    color : str
        Line color in hex
    
    Returns:
    --------
    fig, ax : Figure and Axes objects
    """
    fig, ax = plt.subplots(figsize=(8, 5))
    
    # Plot the main data
    ax.plot(x, y, color=color, linewidth=2.5)
    
    # Add labels and title
    if xlabel:
        ax.set_xlabel(xlabel, fontsize=12)
    if ylabel:
        ax.set_ylabel(ylabel, fontsize=12)
    if title:
        ax.set_title(title, fontsize=14, fontweight='bold')
    
    # Customize the plot appearance
    ax.spines['top'].set_visible(False)
    ax.spines['right'].set_visible(False)
    ax.tick_params(labelsize=10)
    
    # Improve layout
    fig.tight_layout()
    
    return fig, ax

# Example usage
x = np.linspace(0, 10, 100)
y = np.sin(x) * np.exp(-0.1 * x)

fig, ax = create_styled_plot(
    x, y, 
    title="Damped Sine Wave", 
    xlabel="Time (s)", 
    ylabel="Amplitude",
    color="#2a7bbd"
)

# Add a grid for better readability
ax.grid(True, linestyle='--', alpha=0.7)

# Optional: Add annotations
ax.annotate('Maximum', xy=(1.6, 0.8), xytext=(3, 0.9),
            arrowprops=dict(facecolor='black', shrink=0.05, width=1.5))

plt.show()
```

## Multiple Subplots

When you need to compare different datasets or views, a grid of subplots is often useful:

```python
def create_subplot_grid(data_list, titles=None, xlabel=None, ylabel=None, 
                        n_cols=2, figsize=(10, 8)):
    """
    Create a grid of subplots for multiple datasets.
    
    Parameters:
    -----------
    data_list : list of tuples
        List of (x, y) data tuples to plot
    titles : list of str
        List of subplot titles
    xlabel, ylabel : str
        Common axis labels
    n_cols : int
        Number of columns in the grid
    figsize : tuple
        Figure size
        
    Returns:
    --------
    fig : Figure object
    """
    n_plots = len(data_list)
    n_rows = (n_plots + n_cols - 1) // n_cols
    
    fig, axes = plt.subplots(n_rows, n_cols, figsize=figsize)
    
    # Flatten the axes array for easy indexing
    if n_rows > 1 or n_cols > 1:
        axes = axes.flatten()
    else:
        axes = [axes]
    
    # Create each subplot
    for i, (x, y) in enumerate(data_list):
        if i < n_plots:
            ax = axes[i]
            ax.plot(x, y, linewidth=2)
            
            # Add title if provided
            if titles and i < len(titles):
                ax.set_title(titles[i])
                
            # Add common labels only to outer plots
            if i % n_cols == 0 and ylabel:  # Left edge
                ax.set_ylabel(ylabel)
            if i >= (n_rows-1) * n_cols and xlabel:  # Bottom edge
                ax.set_xlabel(xlabel)
            
            # Remove top and right spines
            ax.spines['top'].set_visible(False)
            ax.spines['right'].set_visible(False)
    
    # Hide any unused subplots
    for i in range(n_plots, n_rows * n_cols):
        axes[i].axis('off')
    
    plt.tight_layout()
    return fig

# Example usage
x = np.linspace(0, 10, 100)
data_list = [
    (x, np.sin(x)),
    (x, np.cos(x)),
    (x, np.sin(2*x)),
    (x, np.cos(2*x)),
    (x, np.sin(x) * np.cos(x))
]

titles = ['sin(x)', 'cos(x)', 'sin(2x)', 'cos(2x)', 'sin(x)cos(x)']

fig = create_subplot_grid(
    data_list, 
    titles=titles,
    xlabel='x',
    ylabel='y',
    n_cols=2
)

plt.show()
```

## Usage Notes

1. These functions are designed to work with Matplotlib 3.x and Seaborn
2. For publication-quality figures, save using:
   ```python
   fig.savefig('figure.pdf', dpi=300, bbox_inches='tight')
   ```
3. For web usage, PNG format is usually more appropriate:
   ```python
   fig.savefig('figure.png', dpi=150, bbox_inches='tight')
   ```

You can find more examples and the full source code in my [GitHub repository](https://github.com/yourusername/data-viz-tools). 