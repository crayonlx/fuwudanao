# Markdown 语法：数学公式

云雀使用 [**KaTex**](https://khan.github.io/KaTeX/) 库生成 *LaTeX* 数学公式。

行内的数学公式采用`$`标识，比如 $\sqrt{3x-1}+(1+x)^2$ 。


```
行内的数学公式两端采用`$`标识，比如 $\sqrt{3x-1}+(1+x)^2$ 。
```

数学公式的区块采用`$$`标识，下面是一些例子。

$$
x = {-b \pm \sqrt{b^2-4ac} \over 2a}.
$$

```
$$
x = {-b \pm \sqrt{b^2-4ac} \over 2a}.
$$
```

$$
\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.
$$

```
$$
\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.
$$
```

$$
        \begin{matrix}
        1 & x & x^2 \\
        1 & y & y^2 \\
        1 & z & z^2 \\
        \end{matrix}
$$

```
$$
        \begin{matrix}
        1 & x & x^2 \\
        1 & y & y^2 \\
        1 & z & z^2 \\
        \end{matrix}
$$
```

$$ \left[
    \begin{array}{cc|c}
      1&2&3\\
      4&5&6
    \end{array}
\right] $$

```
$$ \left[
    \begin{array}{cc|c}
      1&2&3\\
      4&5&6
    \end{array}
\right] $$
```

$$
f(x) = \int_{-\infty}^\infty
    \hat f(\xi)\,e^{2 \pi i \xi x}
    \,d\xi
$$

```
$$
f(x) = \int_{-\infty}^\infty
    \hat f(\xi)\,e^{2 \pi i \xi x}
    \,d\xi
$$
```

参考链接

- [Latex 语法](http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference) 
- [Katex 支持的 Latex 命令](https://github.com/Khan/KaTeX/wiki/Function-Support-in-KaTeX)
