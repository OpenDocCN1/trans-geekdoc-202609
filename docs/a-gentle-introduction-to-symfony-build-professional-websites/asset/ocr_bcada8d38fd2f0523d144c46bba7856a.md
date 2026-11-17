If changing data in the model or in the session forces you to erase the cache for the sake of coherence, you can do it with a fine granularity for optimum performance—erase only the elements that have changed, and keep the others.

Remember to test all the pages where caching is enabled with extra care, as new bugs may appear if you cache the wrong elements or if you forget to clear the cache when you update the underlying data. A staging environment, dedicated to cache testing, is of great use for that purpose.

Finally, make the best of the HTTP 1.1 protocol with symfony’s advanced cache-tweaking features, which will involve the client in the caching task and provide even more performance gains.