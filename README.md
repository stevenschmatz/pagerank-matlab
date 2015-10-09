# PageRank in MATLAB

A MATLAB implementation of the Google PageRank algorithm.

```matlab
function [ x ] = PageRank( i, j, n, p )
%PAGERANK Calculates the PageRank of the given network.
%   param i: Vector of all nodes which are linked to.
%   param j: Vector of all nodes which link to other nodes.
%   param n: Number of nodes
%   param p: Decay rate (optional)
%   Note: Node i[k] links to node j[k].

if (~exist('p', 'var'))
    p = 0.85;
end

G = sparse(i, j, 1, n, n);
c = sum(G, 1);
k = find(c~=0);
D = sparse(k,k,1./c(k),n,n);
e = ones(n, 1);
I = speye(n, n);
x = (I - p*G*D)\e;
x = x/sum(x);

end
```
