.. currentmodule:: torch.sparse

torch.sparse
============

.. warning::

    This API is currently experimental and may change in the near future.

Torch supports sparse tensors in COO(rdinate) format, which can
efficiently store and process tensors for which the majority of elements
are zeros.

A sparse tensor is represented as a pair of dense tensors: a tensor
which contains the actual values :class:`torch.sparse.values`, and a
tensor which contains the coordinates of those values
:class:`torch.sparse.indices`.  A sparse tensor can be constructed
by providing these two tensors, as well as the size of the sparse tensor
(which cannot be inferred from these tensors!)

    >>> i = torch.LongTensor([[0, 1], [2, 0]])
    >>> v = torch.FloatTensor([3, 4])
    >>> torch.sparse.FloatTensor(i, v, torch.Size([2,3])).to_dense()
     0  0  3
     4  0  0
    [torch.FloatTensor of size 2x2]

You can also construct hybrid sparse tensors, where only the first n
dimensions are sparse, and the rest of the dimensions are dense.

    >>> i = torch.LongTensor([[2, 4]])
    >>> v = torch.FloatTensor([[1, 3], [5, 7]])
    >>> torch.sparse.FloatTensor(i, v).to_dense()
     0  0
     0  0
     1  3
     0  0
     5  7
    [torch.FloatTensor of size 5x2]

An empty sparse tensor can be constructed by specifying its size:

    >>> torch.sparse.FloatTensor(2, 3)
    SparseFloatTensor of size 2x3 with indices:
    [torch.LongTensor with no dimension]
    and values:
    [torch.FloatTensor with no dimension]

Sparse tensors can have duplicate entries for an index; such a tensor is
called non-coalesced.  Duplicate entries are summed together when
coalescing (or converting to another representation).  Some operations
(for example, :func:`torch.FloatTensor.add`) produce duplicate entries;
if you repeatedly perform these operations, you should coalesce your
sparse tensors to prevent them from growing too large.

.. class:: FloatTensor()

    .. method:: add
    .. method:: add_
    .. method:: clone
    .. method:: contiguous
    .. method:: dim
    .. method:: div
    .. method:: div_
    .. method:: get_device
    .. method:: hspmm
    .. method:: indices
    .. method:: is_contiguous
    .. method:: mm
    .. method:: mul
    .. method:: mul_
    .. method:: nnz
    .. method:: resizeAs_
    .. method:: size
    .. method:: spadd
    .. method:: sparse_mask
    .. method:: spmm
    .. method:: sspaddmm
    .. method:: sspmm
    .. method:: sub
    .. method:: sub_
    .. method:: t_
    .. method:: toDense
    .. method:: transpose
    .. method:: transpose_
    .. method:: values
    .. method:: zero_
