# Graph-Theory
(https://www.overleaf.com/project/6af7129fcd4450bc96c9ca33/share#6d25d62972542238a8a8880c627d6308de3330994148c546)

\documentclass[11pt,a4paper]{article}

% ---------- Packages ----------
\usepackage[margin=1in]{geometry}
\usepackage[T1]{fontenc}
\usepackage{lmodern}
\usepackage{amsmath,amssymb}
\usepackage{tikz}
\usepackage{float}
\usepackage{booktabs}
\usepackage{enumitem}
\usepackage{hyperref}
\usepackage{xcolor}
\usepackage{setspace}

\usetikzlibrary{arrows.meta,positioning,calc}

\hypersetup{
    colorlinks=true,
    linkcolor=blue,
    citecolor=blue,
    urlcolor=blue
}

\setstretch{1.15}
\setlist[itemize]{leftmargin=1.5em}

% ---------- TikZ styles ----------
\tikzset{
    vertex/.style={
        circle, draw=black, fill=blue!12,
        minimum size=7mm, inner sep=1pt, thick
    },
    smallvertex/.style={
        circle, draw=black, fill=blue!12,
        minimum size=6mm, inner sep=1pt, thick
    },
    edge/.style={thick},
    arrowedge/.style={thick, -{Stealth[length=2.5mm]}},
    bestedge/.style={very thick, red!75!black}
}

% ---------- Title ----------
\title{\textbf{Visualization of Different Types of Graphs}\\
\large A Beginner-Friendly Study of Graph Theory Using LaTeX}
\author{}\\
\date{}

\begin{document}
\maketitle

\begin{abstract}
Graph theory is a part of discrete mathematics that studies objects and the
connections between them. In this paper, graphs are explained using simple
examples such as friends, roads, websites, and computer networks. Different
types of graphs are drawn using LaTeX and TikZ. Two practical case studies
show how graph theory can help find a short road route and understand links
between web pages. The aim is to make the topic easy for beginners.
\end{abstract}

\tableofcontents
\newpage

\section{Introduction}

Imagine that you have five friends. You are friends with some of them, and
they are friends with some others. We can draw every person as a dot and
draw a line between two people who are friends. This drawing is called a
\textbf{graph}.

Graph theory is the study of these dots and connections. It is useful because
many real-life situations can be represented in this simple way.

A graph is written as
\[
G=(V,E)
\]
where:
\begin{itemize}
    \item $G$ means the graph.
    \item $V$ is the set of vertices (dots or points).
    \item $E$ is the set of edges (lines or arrows joining the dots).
\end{itemize}

For example, if
\[
V=\{A,B,C\}, \qquad E=\{\{A,B\},\{B,C\}\},
\]
then A is connected to B, and B is connected to C.

\section{A Little Background: Where Did Graph Theory Begin?}

One famous starting point of graph theory is the Seven Bridges of
K\"onigsberg problem. In the eighteenth century, people asked whether they
could walk through a city and cross each of its seven bridges exactly once.
Mathematician Leonhard Euler studied the problem in 1736. He represented
land areas as dots and bridges as connections. This way of thinking helped
create the foundations of graph theory \cite{euler}.

The important lesson is that we do not always need every detail of a real
place. We can keep only the important information:
\begin{itemize}
    \item A place or object becomes a vertex.
    \item A connection or relationship becomes an edge.
\end{itemize}

Today, graph theory is used in road maps, social networks, computer networks,
web searches, transport planning, and many other areas \cite{applications,mit}.

\section{Basic Words You Must Know}

\begin{itemize}
    \item \textbf{Vertex:} One dot in a graph. Example: one city.
    \item \textbf{Edge:} A connection between two vertices. Example: a road.
    \item \textbf{Adjacent vertices:} Two vertices joined directly by an edge.
    \item \textbf{Degree:} The number of edges touching a vertex.
    \item \textbf{Path:} A route that follows connected edges.
    \item \textbf{Cycle:} A path that comes back to its starting vertex.
    \item \textbf{Connected graph:} Every vertex can be reached from every
          other vertex.
    \item \textbf{Disconnected graph:} At least one part is separated from
          another part.
\end{itemize}

\subsection*{A tiny example of degree}

If vertex B has three lines touching it, then its degree is 3:
\[
\deg(B)=3.
\]
Think of degree as counting how many roads meet at a junction.

\section{Different Types of Graphs}

\subsection{Simple Undirected Graph}

An undirected graph has lines without arrows. This means the connection
works both ways. A simple graph has no loops and no repeated edges.

\textbf{Easy example:} If A and B are friends, then B is also a friend of A.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,0) {A};
\node[vertex] (B) at (2,1) {B};
\node[vertex] (C) at (4,0) {C};
\node[vertex] (D) at (2,-1.5) {D};
\draw[edge] (A)--(B);
\draw[edge] (B)--(C);
\draw[edge] (A)--(D);
\draw[edge] (D)--(C);
\draw[edge] (B)--(D);
\end{tikzpicture}
\caption{A simple undirected graph}
\end{figure}

\subsection{Directed Graph}

A directed graph has arrows. The arrow tells us the direction of the
connection. A connection from A to B does not automatically mean there is
a connection from B to A.

\textbf{Easy example:} A follows B on a social-media platform. B may or may
not follow A.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,0) {A};
\node[vertex] (B) at (2,1) {B};
\node[vertex] (C) at (4,0) {C};
\node[vertex] (D) at (2,-1.5) {D};
\draw[arrowedge] (A)--(B);
\draw[arrowedge] (B)--(C);
\draw[arrowedge] (D)--(B);
\draw[arrowedge] (A)--(D);
\end{tikzpicture}
\caption{A directed graph: arrows show the direction}
\end{figure}

\subsection{Weighted Graph}

A weighted graph has a number written on each edge. The number can represent
distance, time, cost, or some other measurement.

\textbf{Easy example:} A road between two towns may be 5 kilometres long.
The number 5 is the weight of that edge.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,0) {A};
\node[vertex] (B) at (2,1.3) {B};
\node[vertex] (C) at (4,0) {C};
\node[vertex] (D) at (2,-1.3) {D};
\draw[edge] (A)-- node[above left] {4 km} (B);
\draw[edge] (B)-- node[above right] {3 km} (C);
\draw[edge] (A)-- node[below left] {6 km} (D);
\draw[edge] (D)-- node[below right] {2 km} (C);
\draw[edge] (B)-- node[right] {5 km} (D);
\end{tikzpicture}
\caption{A weighted graph}
\end{figure}

\subsection{Complete Graph}

A complete graph is a graph in which every vertex is directly connected to
every other vertex. It is written as $K_n$, where $n$ is the number of
vertices.

For example, in $K_4$, there are four vertices and every pair is connected.
The number of edges is
\[
|E|=\frac{n(n-1)}{2}.
\]
For $K_4$:
\[
|E|=\frac{4(4-1)}{2}=6.
\]

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,0) {A};
\node[vertex] (B) at (3,0) {B};
\node[vertex] (C) at (3,2.4) {C};
\node[vertex] (D) at (0,2.4) {D};
\draw[edge] (A)--(B);
\draw[edge] (B)--(C);
\draw[edge] (C)--(D);
\draw[edge] (D)--(A);
\draw[edge] (A)--(C);
\draw[edge] (B)--(D);
\end{tikzpicture}
\caption{Complete graph $K_4$: all six possible edges are present}
\end{figure}

\subsection{Bipartite Graph}

A bipartite graph divides its vertices into two separate groups. Edges can
join a vertex from the first group to a vertex from the second group, but
there are no edges within the same group.

\textbf{Easy example:} One group contains students and the other group
contains courses. A line means that a student is enrolled in a course.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,2) {$S_1$};
\node[vertex] (B) at (0,0) {$S_2$};
\node[vertex] (X) at (3,2.5) {$C_1$};
\node[vertex] (Y) at (3,1) {$C_2$};
\node[vertex] (Z) at (3,-0.5) {$C_3$};
\draw[edge] (A)--(X);
\draw[edge] (A)--(Y);
\draw[edge] (A)--(Z);
\draw[edge] (B)--(X);
\draw[edge] (B)--(Y);
\draw[edge] (B)--(Z);
\node at (0,-1.1) {Students};
\node at (3,-1.1) {Courses};
\end{tikzpicture}
\caption{A complete bipartite graph $K_{2,3}$}
\end{figure}

\subsection{Path Graph}

A path graph is a graph in which vertices are connected one after another
in a line. It has no branches and no cycles.

\textbf{Easy example:} Walking from your home to school through a sequence
of places.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,0) {A};
\node[vertex] (B) at (1.5,0) {B};
\node[vertex] (C) at (3,0) {C};
\node[vertex] (D) at (4.5,0) {D};
\node[vertex] (E) at (6,0) {E};
\draw[edge] (A)--(B)--(C)--(D)--(E);
\end{tikzpicture}
\caption{Path graph $P_5$}
\end{figure}

\subsection{Cycle Graph}

A cycle graph connects the last vertex back to the first vertex. It forms
a closed loop.

\textbf{Easy example:} A circular walking track.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (90:1.7) {A};
\node[vertex] (B) at (18:1.7) {B};
\node[vertex] (C) at (-54:1.7) {C};
\node[vertex] (D) at (-126:1.7) {D};
\node[vertex] (E) at (162:1.7) {E};
\draw[edge] (A)--(B)--(C)--(D)--(E)--(A);
\end{tikzpicture}
\caption{Cycle graph $C_5$}
\end{figure}

\subsection{Tree Graph}

A tree is a connected graph with no cycles. It often looks like a family
tree, with one point branching into smaller branches.

\textbf{Easy example:} A folder structure on a computer, where one main
folder contains smaller folders.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,2.5) {A};
\node[vertex] (B) at (-2,1) {B};
\node[vertex] (C) at (2,1) {C};
\node[vertex] (D) at (-3, -0.5) {D};
\node[vertex] (E) at (-1, -0.5) {E};
\node[vertex] (F) at (1, -0.5) {F};
\node[vertex] (G) at (3, -0.5) {G};
\draw[edge] (A)--(B);
\draw[edge] (A)--(C);
\draw[edge] (B)--(D);
\draw[edge] (B)--(E);
\draw[edge] (C)--(F);
\draw[edge] (C)--(G);
\end{tikzpicture}
\caption{A tree graph}
\end{figure}

A tree with $n$ vertices has exactly $n-1$ edges.

\subsection{Disconnected Graph}

A disconnected graph has two or more separate groups of vertices. There is
no path from one group to another.

\textbf{Easy example:} Two groups of people who have no connection with
each other in the network being studied.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,0) {A};
\node[vertex] (B) at (1.5,1) {B};
\node[vertex] (C) at (1.5,-1) {C};
\node[vertex] (D) at (4,0) {D};
\node[vertex] (E) at (5.5,1) {E};
\node[vertex] (F) at (5.5,-1) {F};
\draw[edge] (A)--(B);
\draw[edge] (A)--(C);
\draw[edge] (D)--(E);
\draw[edge] (D)--(F);
\end{tikzpicture}
\caption{A disconnected graph with two components}
\end{figure}

\subsection{Planar Graph}

A planar graph is a graph that can be drawn on a flat surface without
edges crossing. The drawing may look different, but the connections
between vertices must stay the same.

\textbf{Easy example:} A simple road map drawn without bridges crossing
at the same level.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,0) {A};
\node[vertex] (B) at (3,0) {B};
\node[vertex] (C) at (3,2.4) {C};
\node[vertex] (D) at (0,2.4) {D};
\draw[edge] (A)--(B)--(C)--(D)--(A);
\draw[edge] (A)--(C);
\end{tikzpicture}
\caption{A planar drawing of $K_4$}
\end{figure}

\subsection{Multigraph}

A multigraph allows more than one edge between the same pair of vertices.
Depending on the definition being used, it may also allow loops.

\textbf{Easy example:} Two towns may be joined by both a railway line and
a road. These are two different connections between the same towns.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,0) {A};
\node[vertex] (B) at (3,0) {B};
\draw[edge] (A) to[bend left=25] (B);
\draw[edge] (A) to[bend right=25] (B);
\end{tikzpicture}
\caption{A multigraph with two edges between A and B}
\end{figure}

\section{Where Are Graphs Used in Real Life?}

Graph theory is not only for mathematics exams. It is used to understand
real systems.

\begin{itemize}
    \item \textbf{Google and web pages:} Web pages can be treated as vertices.
          A hyperlink from one page to another is a directed edge.
    \item \textbf{Road maps:} Junctions are vertices and roads are edges.
          Road distances or travel times can be written as weights.
    \item \textbf{Social networks:} People are vertices and friendships or
          follows are edges.
    \item \textbf{Computer networks:} Computers or routers are vertices,
          and communication links are edges.
    \item \textbf{College course planning:} Subjects or tasks can be
          connected by prerequisite relationships.
    \item \textbf{Matching:} A bipartite graph can represent students and
          the courses or projects they can be assigned to.
\end{itemize}

These are standard examples discussed in computer-science and transport
network materials \cite{applications,mit,iitb}.

\section{Practical Case Study 1: Finding a Short Road Route}

Suppose a student wants to travel from place A to place E. The roads and
their distances are shown below. Each number is the distance in kilometres.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,0) {A};
\node[vertex] (B) at (2,1.5) {B};
\node[vertex] (C) at (2,-1.5) {C};
\node[vertex] (D) at (4,1.5) {D};
\node[vertex] (E) at (6,0) {E};

\draw[edge] (A)-- node[above left] {4} (B);
\draw[bestedge] (A)-- node[below left] {2} (C);
\draw[bestedge] (C)-- node[left] {1} (B);
\draw[bestedge] (B)-- node[above] {5} (D);
\draw[edge] (C)-- node[below] {8} (D);
\draw[edge] (C)-- node[below right] {10} (E);
\draw[bestedge] (D)-- node[above right] {2} (E);
\end{tikzpicture}
\caption{An example weighted road network. The red route is the shortest route.}
\end{figure}

We compare a few possible routes:

\begin{center}
\begin{tabular}{lll}
\toprule
Route & Calculation & Total distance \\
\midrule
A--B--D--E & $4+5+2$ & 11 km \\
A--C--D--E & $2+8+2$ & 12 km \\
A--C--B--D--E & $2+1+5+2$ & \textbf{10 km} \\
\bottomrule
\end{tabular}
\end{center}

Therefore, the shortest route in this example is
\[
A\rightarrow C\rightarrow B\rightarrow D\rightarrow E
\]
and its total distance is
\[
2+1+5+2=\boxed{10\text{ km}}.
\]

\textbf{What did we learn?} A weighted graph helps us compare routes.
Algorithms such as Dijkstra's algorithm can find a shortest route in a
network with non-negative edge weights. Transportation engineering uses
graph models and shortest-path methods for road and public-transport
networks \cite{iitb,roadpaper}.

\section{Practical Case Study 2: How Web Pages Link to Each Other}

Think of four web pages named A, B, C, and D. If page A contains a link to
page B, draw an arrow from A to B.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,1.5) {Page A};
\node[vertex] (B) at (3,1.5) {Page B};
\node[vertex] (C) at (3,-1) {Page C};
\node[vertex] (D) at (0,-1) {Page D};
\draw[arrowedge] (A)--(B);
\draw[arrowedge] (A)--(C);
\draw[arrowedge] (B)--(C);
\draw[arrowedge] (C) to[bend left=18] (A);
\draw[arrowedge] (D)--(C);
\end{tikzpicture}
\caption{A small directed web-page network}
\end{figure}

In this example:
\begin{itemize}
    \item A links to B and C.
    \item B links to C.
    \item C links to A.
    \item D links to C.
\end{itemize}

A search engine can study the link structure of web pages. The original
PageRank research by Brin and Page described using the web's hyperlink
structure to help estimate the importance of pages \cite{pagerank}.

\textbf{What did we learn?} A directed graph can represent links between
web pages. The arrows show which page points to which other page.

\section{Practical Case Study 3: A Small Friendship Network}

Imagine six students in a class. Each student is represented by a vertex.
A line means that two students are friends in this example.

\begin{figure}[H]
\centering
\begin{tikzpicture}
\node[vertex] (A) at (0,1) {Anu};
\node[vertex] (B) at (2,2) {Bala};
\node[vertex] (C) at (4,1) {Chitra};
\node[vertex] (D) at (0,-1) {Deepa};
\node[vertex] (E) at (2,-2) {Esha};
\node[vertex] (F) at (4,-1) {Farhan};
\draw[edge] (A)--(B);
\draw[edge] (A)--(D);
\draw[edge] (B)--(C);
\draw[edge] (B)--(E);
\draw[edge] (C)--(F);
\draw[edge] (D)--(E);
\draw[edge] (E)--(F);
\end{tikzpicture}
\caption{An example undirected friendship network}
\end{figure}

The degree of a student tells us how many direct connections that student
has in this small example. For instance, Bala is connected to Anu, Chitra,
and Esha, so
\[
\deg(\text{Bala})=3.
\]

\textbf{What did we learn?} Graphs can help describe groups and connections.
A real social-network study should also respect people's privacy and should
not assume that a person's number of connections tells us everything about
them.

\section{Advantages of Graph Theory}

\begin{itemize}
    \item It makes complicated connections easier to understand.
    \item It helps find routes between places.
    \item It can represent computer and communication networks.
    \item It helps study relationships and connections.
    \item It supports algorithms used in planning and problem-solving.
\end{itemize}

\section{Conclusion}

Graph theory is a useful part of discrete mathematics. It represents
objects as vertices and connections as edges. Different graph types are
useful for different situations: directed graphs show one-way links,
weighted graphs show distance or cost, trees show branching structures,
and bipartite graphs show relationships between two groups.

The road-route example showed how a weighted graph can help compare
distances. The web-page example showed how a directed graph can represent
hyperlinks. These examples explain why graph theory is important in
mathematics, computer science, and everyday technology.

\section*{Quick Revision Table}

\begin{center}
\begin{tabular}{p{3.2cm}p{8.5cm}}
\toprule
\textbf{Graph type} & \textbf{Remember it like this} \\
\midrule
Undirected graph & A line with no arrow; the connection works both ways. \\
Directed graph & An arrow shows the direction. \\
Weighted graph & A number on an edge shows distance, time, or cost. \\
Complete graph & Every vertex is connected to every other vertex. \\
Bipartite graph & Vertices are divided into two groups. \\
Path graph & Vertices form a line or route. \\
Cycle graph & The route comes back to its starting point. \\
Tree graph & A connected branching graph with no cycles. \\
Disconnected graph & The graph has separate parts. \\
Planar graph & It can be drawn without edge crossings. \\
Multigraph & More than one edge may join the same pair of vertices. \\
\bottomrule
\end{tabular}
\end{center}

\begin{thebibliography}{9}

\bibitem{euler}
Mathematical Association of America,
\textit{Leonard Euler's Solution to the Konigsberg Bridge Problem}.
Available at:
\url{https://old.maa.org/press/periodicals/convergence/leonard-eulers-solution-to-the-konigsberg-bridge-problem}

\bibitem{applications}
OpenDSA,
\textit{Graphs Chapter Introduction}.
Available at:
\url{https://opendsa-server.cs.vt.edu/ODSA/Books/CS3/html/GraphIntro.html}

\bibitem{mit}
Massachusetts Institute of Technology,
\textit{Decomposition, Abstraction, Functions: Graphs Model a Wide Range of Systems}.
Available at:
\url{https://introcomp.mit.edu/_static/spring26/download/lec11-slides.pdf}

\bibitem{iitb}
T. V. Mathew, IIT Bombay,
\textit{Transportation Networks: Lecture Notes in Transportation Systems Engineering}.
Available at:
\url{https://www.civil.iitb.ac.in/tvm/nptel/702_Networks/web/web.html}

\bibitem{pagerank}
S. Brin and L. Page,
\textit{The Anatomy of a Large-Scale Hypertextual Web Search Engine},
Computer Networks and ISDN Systems, 30 (1998), pp. 107--117.
Available at:
\url{https://courses.cs.duke.edu/common/compsci092/papers/google/pagerank.pdf}

\bibitem{roadpaper}
Z. Grujic and B. Grujic,
\textit{Optimal Routing in Urban Road Networks: A Graph-Based Approach Using
Dijkstra's Algorithm}, Applied Sciences, 15(8), 4162 (2025).
Available at:
\url{https://www.mdpi.com/2076-3417/15/8/4162}

\end{thebibliography}

\end{document}
